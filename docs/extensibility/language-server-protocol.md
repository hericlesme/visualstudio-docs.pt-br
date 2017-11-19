---
title: "Visão geral do protocolo de servidor de idioma | Microsoft Docs"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aeef820575a4fb055318fe11d401e85c9958bad
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="language-server-protocol"></a>Protocolo de idioma do servidor

## <a name="what-is-the-language-server-protocol"></a>O que é o protocolo de servidor de idioma?

Autoconclusões de código fonte, como suporte avançados recursos de edição ou **ir para definição** para uma linguagem de programação em um editor ou IDE é tradicionalmente muito difícil e demorado. Geralmente ele requer a criação de um modelo de domínio (um scanner, um analisador, um verificador de tipo, um construtor e muito mais) na linguagem de programação do IDE ou editor. Por exemplo, o plug-in Eclipse CDT, que fornece suporte para C/C++ no IDE do Eclipse é gravado em Java, desde que o IDE do Eclipse em si é gravado em Java. Seguir essa abordagem, isso significaria implementar um modelo de domínio do C/C++ em TypeScript para Visual Studio Code e um modelo de domínio separadas em c# para o Visual Studio.

Criação de modelos de domínio específico do idioma também é muito mais fácil se uma ferramenta de desenvolvimento pode reutilizar as bibliotecas existentes específico do idioma. No entanto, essas bibliotecas são normalmente implementadas na linguagem de programação em si (por exemplo, bom C/C++ domínio modelos são implementados em C/C++). Integrar uma biblioteca C/C++ em um editor escrito em TypeScript é tecnicamente possível, mas difícil.

### <a name="language-servers"></a>Servidores de linguagem

Outra abordagem é executar a biblioteca em seu próprio processo e usar a comunicação entre processos para conversar com ele. As mensagens enviadas e para trás formam um protocolo. O protocolo de servidor de idioma (LSP) é o produto de padronização mensagens trocadas entre uma ferramenta de desenvolvimento e um processo de servidor de idioma. Usar servidores de idioma ou demons não é uma ideia novel ou novo. Editores como Vim e Emacs fazendo isso por algum tempo oferecer suporte a semântica de conclusão automática. O objetivo de LSP era simplificar a esses tipos de integrações e fornecem uma estrutura útil para expor os recursos de idioma para uma variedade de ferramentas.

Ter um protocolo comum permite a integração de recursos de linguagem de programação em uma ferramenta de desenvolvimento sem complicações reutilizando uma implementação existente do modelo de domínio do idioma. Um servidor back-end do idioma poderia ser escrito em PHP, Python ou Java e LSP permite facilmente ser integrado em uma variedade de ferramentas. O protocolo funciona em um nível comum de abstração para que uma ferramenta pode oferecer serviços avançados de idioma sem a necessidade de compreender totalmente as nuances específicas para o modelo de domínio subjacente.

## <a name="how-work-on-the-lsp-started"></a>Como funcionam em LSP iniciado

O LSP evolução ao longo do tempo e hoje é a versão 3.0. Ele iniciado quando o conceito de um servidor de idioma foi recebido pelo OmniSharp para fornecer recursos de edição avançados para c#. Inicialmente, OmniSharp usado o protocolo HTTP com uma carga JSON e foi integrado ao vários editores incluindo [código do Visual Studio](https://code.visualstudio.com).

Ao mesmo tempo, a Microsoft começou a trabalhar em um servidor de linguagem TypeScript, com a ideia de suporte para editores como Emacs e texto Sublime TypeScript. Nessa implementação, um editor se comunica por meio de stdin/stdout com o processo de servidor TypeScript e usa uma carga JSON inspirado pelo protocolo do depurador V8 para solicitações e respostas. O servidor de TypeScript foi integrado no código VS e TypeScript Sublime plug-in para TypeScript avançada de edição.

Depois de ter em integrado dois servidores de idioma diferente, a equipe de código VS iniciado para explorar um protocolo de servidor de linguagem comum para editores e IDEs. Um protocolo comum permite que um provedor de linguagem criar um servidor único idioma que pode ser consumido por IDEs diferentes. Um consumidor de servidor de idioma só precisa implementar o lado do cliente do protocolo de uma vez. Isso resulta em uma situação de ganhos para o provedor do idioma e o consumidor de idioma.

Iniciado com o protocolo de idioma usado pelo servidor do TypeScript, era mais geral e neutralidade de idioma. O protocolo foi com mais recursos de idioma usando a API da linguagem de código do VS para inspirei. O próprio protocolo é feito com RPC de JSON para invocação remota devido a suas bibliotecas de simplicidade e suporte para várias linguagens de programação.

O código VS team dogfooded o protocolo com a implementação de vários servidores de idioma linter. Um servidor de idioma linter responde às solicitações para pano (verificação) de um arquivo e retorna um conjunto de erros e avisos detectados. A meta era pano sem um arquivo como as edições do usuário em um documento, o que significa que haverá muitas solicitações de linting durante uma sessão do editor. Fazia sentido manter um servidor de backup e em execução para que um novo processo de linting não precisa ser iniciada para cada edição do usuário. Vários servidores linter foram implementados, incluindo o código de VS extensões ESLint e TSLint. Esses dois servidores linter são ambos implementados em TypeScript/JavaScript e executados em Node. js. Eles compartilham uma biblioteca que implementa a parte do cliente e servidor do protocolo.

## <a name="how-the-lsp-works"></a>Como funciona o LSP

Um servidor de linguagem é executado em seu próprio processo e ferramentas como o Visual Studio ou código VS se comunicar com o servidor usando o protocolo de linguagem via RPC de JSON. Outra vantagem do servidor de idioma que operam em um processo dedicado é evita problemas de desempenho relacionados a um modelo de processo único. O canal de transporte real pode ser stdio, soquetes, pipes nomeados ou nó ipc se o cliente e o servidor são escritos em Node.js.

Abaixo está um exemplo de como uma ferramenta e um servidor de idioma se comunicar durante uma rotina de sessão de edição:

![diagrama de fluxo de LSP](media/lsp-flow-diagram.png)

* **O usuário abre um arquivo (conhecido como um documento) na ferramenta**: A ferramenta notifica o servidor de idioma que um documento está aberto (' textDocument/didOpen'). De agora em diante, na verdade sobre o conteúdo do documento não está mais no sistema de arquivos, mas mantidos pela ferramenta na memória.

* **O usuário fizer edições**: A ferramenta notifica o servidor sobre a alteração do documento (' textDocument/didChange') e as informações de semânticas do programa são atualizadas pelo servidor de idioma. Quando isso acontece, o servidor de idioma analisa essas informações e notifica a ferramenta com os erros detectados e avisos (' textDocument/publishDiagnostics').

* **O usuário executa "Ir para definição" em um símbolo no editor de**: A ferramenta envia uma solicitação de ' textDocument/definição de' com dois parâmetros: (1) o URI do documento e (2) a posição do texto a partir de onde ir para solicitação de definição foi iniciada no servidor. O servidor responde com o URI do documento e a posição da definição do símbolo dentro do documento.

* **O usuário fecha o documento (arquivo)**: é enviada uma notificação de ' textDocument/didClose' da ferramenta, informando o servidor de idioma que o documento está agora não mais na memória e que o conteúdo atual agora é atualizado no sistema de arquivos.

Este exemplo ilustra como o protocolo se comunica com o servidor de idioma no nível de recursos do editor com "Ir para definição de", "Localizar todas as referências". Tipos de dados usados pelo protocolo são editor ou IDE 'tipos de dados' como o documento de texto aberto no momento e a posição do cursor. Os tipos de dados não estão no nível de um modelo de domínio programação do idioma que normalmente seria fornecem árvores de sintaxe abstrata e símbolos do compilador (por exemplo, os tipos resolvidos, namespaces,...). Isso simplifica o protocolo significativamente.

Agora vamos dar uma olhada na solicitação ' textDocument/definição de' em mais detalhes. Abaixo estão as cargas que vão entre a ferramenta de cliente e o servidor de idioma para a solicitação de "Ir para definição" em um documento de C++.

Esta é a solicitação:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Esta é a resposta:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Em retrospecto, descrevendo os tipos de dados no nível do editor em vez de no nível do modelo de linguagem de programação é um dos motivos para o sucesso do protocolo do servidor de idioma. É muito mais simples padronizar um URI do documento de texto ou uma posição de cursor em comparação com a padronização um símbolos de compilador e de árvore de sintaxe abstrata em linguagens de programação diferentes.

Quando um usuário está trabalhando com idiomas diferentes, o código VS normalmente inicia um servidor de idioma para cada linguagem de programação. O exemplo a seguir mostra uma sessão em que o usuário trabalha em Java e SASS arquivos.

![Java e sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Capacidades

Nem todo servidor de idioma pode dar suporte a todos os recursos definidos pelo protocolo. Portanto, o cliente e o servidor apresenta seu conjunto de recursos com suporte por meio de 'recursos'. Por exemplo, um servidor de anuncia que ele possa manipular a solicitação ' textDocument/definição de', mas ele não pode manipular a solicitação de 'espaço de trabalho/symbol'. Da mesma forma, os clientes podem anunciar que eles sejam capazes de fornecer ' prestes a salvar' notificações antes de um documento é salvo, para que um servidor pode calcular edições textuais para formatar automaticamente o documento editado.

## <a name="integrating-a-language-server"></a>Integração de um servidor de idioma

A integração real de um servidor de idioma em uma determinada ferramenta não está definida pelo protocolo do idioma do servidor e é da esquerda para as implementações de ferramenta. Algumas ferramentas integram os servidores de idioma genericamente por ter uma extensão que pode iniciar e se comunicar com qualquer tipo de servidor de idioma. Outras, como código VS, criam uma extensão personalizada por servidor de idioma, para que uma extensão ainda possa fornecer alguns recursos de idioma personalizado.

Para simplificar a implementação de clientes e servidores de idioma, há bibliotecas ou SDKs para as partes do cliente e servidor. Essas bibliotecas são fornecidas para diferentes idiomas. Por exemplo, há um [idioma cliente npm módulo](https://www.npmjs.com/package/vscode-languageclient) para facilitar a integração de um servidor de idioma em uma extensão de código VS e outro [módulo de npm de servidor de idioma](https://www.npmjs.com/package/vscode-languageserver) para gravar um servidor de idioma usando Node. js. Isso é atual [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) das bibliotecas de suporte.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Usando o protocolo de servidor de linguagem do Visual Studio

* [Adicionar uma extensão do protocolo de servidor de idioma](adding-an-lsp-extension.md) -Saiba mais sobre como integrar um servidor de idioma para o Visual Studio.
