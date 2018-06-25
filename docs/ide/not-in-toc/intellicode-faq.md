---
title: Perguntas e respostas sobre o IntelliCode
ms.date: 05/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: f0410b3ffd04c42f316d99c150253e72bb1b1944
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34468798"
---
# Perguntas Frequentes sobre o Visual Studio IntelliCode

Obrigado por seu interesse no Visual Studio IntelliCode! Fornecemos essas breves Perguntas Frequentes para tentar responder a algumas das dúvidas que você pode ter.

## P. O que é o Visual Studio IntelliCode?

No build de 2018, anunciamos o Visual Studio IntelliCode, uma nova funcionalidade que aprimora o desenvolvimento de software usando IA. O IntelliCode ajuda desenvolvedores e equipes a escrever código com confiança, localizar problemas mais rapidamente e concentrar revisões de código.

Fornecemos uma visão antecipada de como o IntelliCode melhora o processo de desenvolvimento de software das seguintes maneiras:

- Fornece conclusões de código com percepção de contexto
- Orienta os desenvolvedores a aderir aos padrões e estilos de sua equipe
- Encontra problemas de código difíceis de detectar
- Concentra revisões de código chamando atenção para áreas que realmente importam

Os desenvolvedores podem encontrar mais informações e se inscrever para receber notícias e versões prévias privadas futuras em [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. O que o Visual Studio IntelliCode possibilita que os clientes façam?

O Visual Studio IntelliCode é um conjunto de recursos que oferecem novas melhorias de produtividade por meio de IA (inteligência artificial).

Os desenvolvedores podem [baixar uma extensão experimental](https://go.microsoft.com/fwlink/?linkid=872707) para o Visual Studio 2017 versão 15.7 e posteriores. A extensão fornece IntelliSense avançado que prevê a API que mais provavelmente é a correta para o desenvolvedor usar, em vez de apenas apresentar uma lista de membros em ordem alfabética. Ele usa o contexto de código atual do desenvolvedor e padrões para fornecer essa lista dinâmica. Atualizaremos a extensão com mais recursos nos próximos meses.

## P. Há outras funcionalidades que serão incluídas na extensão do Visual Studio IntelliCode? E quanto à geração de editorconfig?

Estamos trabalhando ativamente em diversos recursos que teremos o prazer de compartilhar publicamente assim que estiverem disponíveis. Demonstramos uma versão interna antecipada de uma ferramenta que infere as configurações de editorconfig quanto ao estilo de código e à formatação no C# no Microsoft Build 2018. Ainda não está na extensão experimental, mas estamos planejando disponibilizá-la nela em breve. Inscreva-se para receber notícias e atualizações em [https://aka.ms/intellicode](https://aka.ms/intellicode) e seja o primeiro a saber quando novas funcionalidades estiverem disponíveis.

## P: O que torna o "IntelliSense assistido por IA" fornecido pelo IntelliCode melhor do que o IntelliSense comum da plataforma?

Com o IntelliCode, a lista de conclusão sugere a API que mais provavelmente é a correta para o desenvolvedor usar, em vez de apresentar uma simples lista de membros em ordem alfabética. Ele usa o contexto de código atual do desenvolvedor e padrões baseados em 2000 projetos de software livre de alta qualidade do GitHub, cada um deles com mais de 100 estrelas, para fornecer essa lista dinâmica. Os resultados formam um modelo que prevê as chamadas à API mais prováveis e mais relevantes.

## P: As sugestões de conclusão do IntelliCode são boas?

Estamos usando as recomendações do IntelliCode internamente na Microsoft há algum tempo e acreditamos que as sugestões são úteis. No entanto, só poderemos confirmar a utilidade dessas recomendações quando vocês a usarem ao codificar. Gostaríamos que vocês experimentassem a [extensão IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) no Visual Studio. Conte-nos como ela funciona para você e envie-nos seus comentários. Também treinaremos nosso modelo com base no que vocês escolherem em nossas recomendações e atualizaremos a extensão conforme o modelo se aperfeiçoa.

> [!NOTE]
> Nenhum código definido pelo usuário é coletado. Confira a pergunta sobre [privacidade](#privacy).

## P. Qual é o futuro do IntelliCode?

Estamos explorando uma ampla gama de maneiras de aumentar a produtividade do desenvolvedor usando IA e outras técnicas avançadas. No Microsoft Build 2018, mostramos uma exibição antecipada de alguns dos cenários em que acreditamos que a IA poderá ajudar os desenvolvedores, mas há muitos outros! Estamos interessados em saber mais dos desenvolvedores que fazem experimentos com o que mostramos, portanto, inscreva-se para receber notícias e atualizações em [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. Quanto custa?

No momento, não temos nenhum anúncio relacionado a preços.

## P. Quando o IntelliCode será lançado?

O IntelliSense assistido por IA do IntelliCode está, atualmente, em sua primeira versão prévia experimental. Continuaremos atualizando a extensão experimental e adicionaremos mais recursos no futuro. Não temos nenhuma agenda para uma versão final, mas apreciamos os comentários de desenvolvedores para que possamos fornecer as melhores experiências possíveis. Você pode se inscrever para receber notícias e atualizações em [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. Essa experiência só está disponível no Visual Studio e para o C#?

A experiência foi mostrada no build 2018 no Visual Studio de 2017 em uma base de código C#. No entanto, estamos ansiosos para expandir o IntelliCode para mais idiomas e ferramentas da família do Visual Studio no futuro.

## P. <a name="whynointellisense"/> Não consigo ver as sugestões do IntelliCode em minha experiência de edição do C#. O que está acontecendo?

As sugestões do IntelliCode são exibidas na experiência padrão do Visual Studio IntelliSense para C#. As extensões que substituem essa experiência impedem a exibição das sugestões "estreladas" do IntelliCode na parte superior da lista. Verifique se as extensões estão causando esse comportamento desativando-as e, em seguida, tentando usar o IntelliSense novamente.

Se isso não resolver o problema para você, relate o problema por meio da funcionalidade [Relatar um Problema](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) do Visual Studio e mencione o IntelliCode no relatório.

## P. Qual versão do Visual Studio é necessária para executar essa extensão?

A extensão IntelliCode do Visual Studio é compatível com o Visual Studio 2017 versão 15.7, versão prévia 5 e posteriores (todas as SKUs). A instalação da extensão será interrompida pela mensagem "Esta extensão não é instalável em nenhum dos produtos atualmente instalados." se a versão mínima exigida não estiver instalada.

## P. Essa experiência só está disponível em inglês?

O IntelliCode é uma extensão em versão prévia hoje, e estamos ansiosos para saber o quanto essas funcionalidades são úteis para um conjunto mais amplo de clientes. Quando o IntelliCode deixar de ser uma versão prévia, certamente consideraremos os locais e idiomas que terão suporte primeiro e como ele será oferecido, com base nos seus comentários.

## <a name="privacy"/> P: E quanto à privacidade? Vocês estão enviando meu código para a nuvem? Quais dados do cliente estão sendo enviados à Microsoft?

Os desenvolvedores são convidados a experimentar o Visual Studio IntelliCode como uma extensão de versão prévia experimental. A finalidade da extensão é permitir que os desenvolvedores testem os recursos do IntelliCode e forneçam comentários à equipe do produto.

Nós coletamos alguns dados anônimos de uso e de relatório de erros da extensão para ajudar a melhorar o produto. Nenhum código definido pelo usuário é enviado à Microsoft, mas nós coletamos informações sobre seu uso dos resultados do IntelliCode. Os dados só incluem os tipos e membros de .NET e de software livre que você selecionou na lista de sugestões do IntelliCode. Os desenvolvedores podem recusar o [Programa de Aperfeiçoamento da Experiência do Visual Studio](../../ide/visual-studio-experience-improvement-program.md), que desativa a coleta de dados para a extensão do IntelliCode também. Na barra de menus, selecione **Ajuda** > **Enviar Comentários** > **Configurações**. Na caixa de diálogo **Programa de Aperfeiçoamento da Experiência do Visual Studio**, selecione **Não, prefiro não participar** e, em seguida, selecione **OK**.

A extensão do IntelliCode pode pedir periodicamente que o desenvolvedor responda uma pesquisa, que também é anônima. Os usuários podem se inscrever para receber notícias e uma versão prévia privada futura. No momento, não é obrigatório que façam isso para usar a extensão experimental.

Recursos futuros podem exigir acesso a um serviço, que exigirá a inscrição. Quando esses recursos estiverem prontos para a versão prévia privada, publicaremos mais detalhes.
