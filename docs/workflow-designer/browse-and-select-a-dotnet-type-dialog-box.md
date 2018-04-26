---
title: Designer de fluxo de trabalho - procurar e selecione uma caixa de diálogo de tipo .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4d136c98acd2719abd07f8feb2f9def48ec6b2ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET

No **propriedades** designers, como o designer de variáveis, quando você seleciona, caixas de diálogo ou janela **procurar tipos...**  em uma lista de tipos de dados, é o **procurar e selecionar um tipo .NET** caixa de diálogo (chamada em uma forma abreviada do navegador"tipo"). Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore de assemblies e de projetos.

 Esta caixa de diálogo é empregada em um número de cenários do usuário, incluindo o seguinte:

-   Ao definir o tipo de uma variável ou um argumento.

-   Ao selecionar um tipo para uma atividade genérico.

-   Para adicionar uma captura na atividade de <xref:System.Activities.Statements.TryCatch> .

> [!NOTE]
> O navegador do tipo pode exibir tipos de jagged array Visual Basic, mas não tipos de matriz multidimensional. Consulte [matrizes denteadas](http://go.microsoft.com/fwlink/?LinkId=195226) e [matrizes multidimensionais](http://go.microsoft.com/fwlink/?LinkId=195227) para obter detalhes.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selecionando um tipo de valor ou tipo de referência de navegador de tipo

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para selecionar um valor ou uma referência digite de navegador de tipo

1.  No **nome do tipo** , digite o nome do tipo que você deseja usar.

2.  Realize um dos seguintes procedimentos:

    -   Depois que o nome do tipo que você deseja usar é exibido na árvore de **nome do tipo** caixa, clique duas vezes o tipo para selecioná-lo.

    -   Digitar caracteres suficientes no **nome do tipo** caixa para identificar exclusivamente o tipo que você deseja usar e, em seguida, pressione enter para selecionar o tipo

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para selecionar um tipo genérico de navegador de tipo

1.  No **nome do tipo** caixa, digite o nome do tipo que você deseja usar.

2.  Depois que o nome do tipo que você deseja usar é exibido na árvore de **nome do tipo** caixa, clique para selecioná-lo para fazer com que as caixas de lista suspensa o tipo é exibido.

     Selecione o tipo que você deseja usar para fechar genérica nas caixas de lista suspensa e, em seguida, clique em **Okey**.

## <a name="types-displayed-in-the-type-browser"></a>Tipos exibidos no navegador de tipo
 Os tipos exibidos no navegador do tipo podem variar dependendo de como o navegador de tipo foi iniciado. Se o navegador de tipo foi iniciado em um projeto de fluxo de trabalho dentro do **vs2010**, por padrão, todos os tipos no assembly referenciado e projetos referenciados são mostrados. Se o navegador de tipo foi iniciado de fora de um **vs2010** projeto sistema (como em um aplicativo de fluxo de trabalho hospedado novamente ou em um arquivo de fluxo de trabalho autônomo), por padrão, os tipos de todos os assemblies carregados no AppDomain são mostradas .

 No navegador de tipo pode ser filtro por desenvolvedores do designer de atividade. Para quaisquer atividades determinada, você pode ver apenas um subconjunto dos tipos. Por exemplo, na atividade de <xref:System.Activities.Statements.TryCatch> , somente os tipos derivados de <xref:System.Exception> são mostrados no navegador do tipo.

## <a name="filtering-search-results-in-the-type-browser"></a>Resultados de pesquisa de filtragem no navegador de tipo
 A lista de tipos no **nome do tipo** caixa obtém menor conforme você digita mais caracteres para localizar uma correspondência. Somente tipos cujo nome totalmente qualificado começa com a cadeia de caracteres que você digitou ou tipos cujo nome curto começa com a cadeia de caracteres que você digitou aparecem na lista filtrada.

 Por exemplo:

1.  Digitar **operação** corresponde <xref:System.OperationCanceledException> mas não <xref:System.InvalidOperationException>. Para corresponder <xref:System.InvalidOperationException>, inicie digite System.I ou inválido.

2.  Digitar **genérico** corresponde <xref:System.GenericUriParser> , mas não tipos no <xref:System.Collections.Generic> namespace. Para procurar por tipos no namespace <xref:System.Collections.Generic> , digite o nome totalmente qualificado do namespace.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selecionando um contrato de serviço usando a caixa de diálogo de navegador de tipo
 Ao selecionar um tipo de contrato de serviço, o navegador do tipo mostra somente os tipos que têm o atributo de <xref:System.ServiceModel.ServiceContractAttribute> .

## <a name="see-also"></a>Consulte também

- [Usando os designers de atividade](../workflow-designer/using-the-activity-designers.md)