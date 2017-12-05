---
title: Ferramentas R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1ff32914b523b2b515a3d4175e4b3f76ad7ecefd
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2017
---
# <a name="working-with-r-in-visual-studio"></a>Trabalho com o R no Visual Studio

O R é uma linguagem altamente extensível e um ambiente para gráficos e computação estatística. Ele é distribuído gratuitamente sob a Licença Pública Geral GNU, dispõe de suporte à comunidade forte e é conhecido por sua capacidade de gerar plotagens de qualidade de publicação incluindo fórmulas e símbolos matemáticos. Você pode saber mais sobre o R em [r-project.org](https://www.r-project.org/about.html) e [Uma introdução ao R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

As Ferramentas R para Visual Studio (RTVS) são uma extensão de [código-fonte aberto](https://github.com/microsoft/RTVS) gratuita para Visual Studio 2017 e Visual Studio 2015 Atualização 3 (ou superior), lançado sob a licença MIT. (Um segundo componente de código-fonte aberto chamado [RHost](https://github.com/microsoft/R-Host), que é vinculado aos binários do interpretador do R, é lançado sob a Licença Pública GNU V2.)

> [!Note]
> Atualmente, as RTVS têm suporte apenas no Visual Studio para Windows, mas não no Visual Studio para Mac.

Para experimentar o R no Visual Studio:

- [Instalar as Ferramentas R](installation.md).
- Siga o guia de [Introdução](getting-started-with-r.md), bem como os tópicos [Exemplos](getting-started-samples.md) e [Obtendo ajuda](getting-started-help.md).

Depois, siga os links abaixo para saber mais sobre recursos relacionados ao R, bem como os próprios recursos gerais do Visual Studio.

| Recurso | Descrição | Documentação geral do Visual Studio | 
| --- | --- | --- |
| [Sistema de projeto do Visual Studio](projects.md) | Organize e gerencie arquivos relacionados em uma estrutura conveniente e aproveite modelos úteis para itens como código do R, documentação do R, Markdown do R, consultas SQL e procedimentos armazenados. Aproveite também o [gerenciador de pacotes](package-manager.md) e a [integração do SQL Server](sql-server.md).  | [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Espaço de trabalho](workspaces.md) | As RTVS podem ser associadas a espaços de trabalho locais e remotos, permitindo que você desenvolva o código R localmente com conjuntos de dados menores, em seguida, execute com facilidade o código em computadores baseados em nuvem mais poderosos com conjuntos de dados muito maiores. | N/D |
| [Opções de Ferramentas R](options.md) | Controle vários aspectos das RTVS. | [Caixa de diálogo de opções](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edição avançada, IntelliSense, e trechos de código](code-editing.md) | Inclui coloração de sintaxe, [IntelliSense](code-intellisense.md) em todo o código e todas as bibliotecas, formatação de código, ajuda da assinatura, comandos Ir Para Definição e Localizar Todas as Referências, [trechos de código](code-snippets.md) e muito mais. | [Escrevendo código no editor de códigos e de texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Markdown do R](rmarkdown.md) | Os documentos de Markdown do R ajudam você a compartilhar os resultados de dados, com código R integrado dentro dos blocos de código de markdown. | N/D |
| [Janela Interativa](interactive-repl.md) | Fornece uma experiência completa de REPL para o R com a capacidade de executar facilmente o código em um arquivo de origem na janela interativa. | N/D |
| [Visualização de dados](visualizing-data.md) | A plotagem é parte integral da experiência do R, e as RTVS oferece suporte a várias janelas de plotagem independentes, cada qual com seu próprio histórico e a capacidade de mover as plotagens entre as janelas. As plotagens podem ser salvas em bitmap e arquivos PDF ou copiadas para a área de transferência como um bitmap ou metarquivo.  | N/D |
| [Gerenciador de Variáveis](variable-explorer.md) | Examine as variáveis em escopos globais ou específicos do pacote, com a possibilidade de exibir tabelas classificáveis e exportar para CSV. | N/D |
| [Depuração completa](debugging.md) | Inclui a integração com a janela interativa. | [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md) |

Confira também as [Perguntas frequentes](faq.md).

O vídeo a seguir também oferece uma breve análise (5m 48s) dos recursos das Ferramentas R:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>Envie-nos seus comentários!

1. **Problemas do Github**: a melhor maneira de alcançar a equipe de RTVS é [registrar um problema no GitHub](https://github.com/Microsoft/RTVS/issues) ou usar o menu **Ferramentas R > Comentários**.

1. **Envie um Smiley/Rosto Triste**: o menu **Ferramentas R > Comentários** é uma maneira rápida de enviar comentários e anexar arquivos de log das RTVS para auxiliar no diagnóstico do seu problema. (Os logs serão registrados nos `%temp%/RTVSlogs.zip` caso você queira enviá-los separadamente.) O log será desabilitado se você tiver cancelado a telemetria do Visual Studio por meio do comando de menu **Ajuda > Comentários > Configurações** ou durante a instalação.

1. **Email**: você pode enviar comentários diretos para a equipe em *rtvsuserfeedback (arroba) microsoft.com*.
