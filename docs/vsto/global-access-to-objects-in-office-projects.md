---
title: Acesso global a objetos em projetos do Office | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 12ae527d52e3dad3c60d561ba3bd5fa1171ac48b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="global-access-to-objects-in-office-projects"></a>Acesso global a objetos em projetos do Office
  Quando você cria um projeto do Office, o Visual Studio gera automaticamente uma classe denominada `Globals` no projeto. Você pode usar o `Globals` classe para acessar vários itens de projeto diferente em tempo de execução de qualquer código no projeto.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Como usar a classe Globals  
 `Globals`é uma classe estática que mantém referências a determinados itens em seu projeto. Usando o `Globals` classe, você pode acessar os seguintes itens de qualquer código no projeto em tempo de execução:  
  
-   O `ThisWorkbook` e `Sheet`  *n*  classes em um projeto de modelo ou pasta de trabalho do Excel. Você pode acessar esses objetos usando o `Globals.ThisWorkbook` e `Sheet`  *n*  propriedades.  
  
-   O `ThisDocument` classe em um projeto de modelo ou documento do Word. Você pode acessar esse objeto usando o `Globals.ThisDocument` propriedade.  
  
-   O `ThisAddIn` classe em um projeto de suplemento do VSTO. Você pode acessar esse objeto usando o `Globals.ThisAddIn` propriedade.  
  
-   Todas as faixas de opções em seu projeto personalizados usando o Designer de faixa de opções. Você pode acessar as faixas de opções usando o `Globals.Ribbons` propriedade. Para obter mais informações, consulte [acessando a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Todas as regiões de formulário Outlook em um projeto de suplemento do VSTO do Outlook. Você pode acessar as regiões de formulário usando o `Globals.FormRegions` propriedade. Para obter mais informações, consulte [acessando uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   Um objeto de fábrica que permite criar controles de faixa de opções e hospedar itens em tempo de execução em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Você pode acessar esse objeto usando o `Globals.Factory` propriedade. Esse objeto é uma instância de uma classe que implementa uma as seguintes interfaces:  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Por exemplo, você pode usar o `Globals.Sheet1` propriedade para inserir texto em uma <xref:Microsoft.Office.Tools.Excel.NamedRange> control em `Sheet1` quando um usuário clica em um botão no painel de ações em um projeto no nível de documento para Excel.  
  
 [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
 [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initializing-the-globals-class"></a>Inicializar a classe Globals  
 Código que tenta usar o `Globals` classe antes do documento ou um suplemento do VSTO está completamente inicializado pode gerar uma exceção de tempo de execução. Por exemplo, usando `Globals` quando declarando uma variável de nível de classe pode falhar porque o `Globals` classe não pode ser inicializada com referências a todos os itens de host antes do objeto declarado é instanciado.  
  
> [!NOTE]  
>  O `Globals` classe nunca é inicializada no tempo de design, mas as instâncias de controle são criadas pelo designer. Isso significa que, se você criar um controle de usuário que usa uma propriedade do `Globals` classe de dentro de uma classe de controle de usuário, você deve se a propriedade retorna **nulo** antes de tentar usar o objeto retornado.  
  
## <a name="see-also"></a>Consulte também  
 [Acessando a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Acessando uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Item de Host do documento](../vsto/document-host-item.md)   
 [Item de Host de pasta de trabalho](../vsto/workbook-host-item.md)   
 [Item de Host de planilha](../vsto/worksheet-host-item.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
  
  