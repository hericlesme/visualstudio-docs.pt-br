---
title: Item de Host de pasta de trabalho | Microsoft Docs
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
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
ms.assetid: 54489d91-a799-4dc2-89b8-498cf17c2f57
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 21017bc63f028bdbd65d27b0df0cba2e31d407ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="workbook-host-item"></a>Item de host da pasta de trabalho
  O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host é um tipo que estende o <xref:Microsoft.Office.Interop.Excel.Workbook> tipo do assembly de interoperabilidade primária para o Excel. O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host fornece todas as mesmas propriedades, métodos e eventos como um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto, mas ele também fornece recursos adicionais.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Em projetos de nível de documento, há um padrão <xref:Microsoft.Office.Tools.Excel.Workbook> item de host que representa a pasta de trabalho em seu projeto. Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Excel.Workbook> itens de host em tempo de execução.  
  
## <a name="understanding-the-workbook-host-item-in-document-level-projects"></a>Noções básicas sobre o Item de Host de pasta de trabalho no nível de documento  
 Para acessar a pasta de trabalho em seu projeto, use o `ThisWorkbook` classe. O `ThisWorkbook` classe fornece acesso a membros de <xref:Microsoft.Office.Tools.Excel.Workbook> item de host para executar tarefas básicas em sua personalização, como executar código quando a pasta de trabalho é aberta ou fechada. Para obter mais informações, consulte [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
 O `ThisWorkbook` classe fornece um local no qual começar a gravar código no seu projeto. Porque a classe fornece todas as mesmas propriedades, métodos e eventos como o <xref:Microsoft.Office.Interop.Excel.Workbook> do objeto no assembly de interoperabilidade primário para o Excel, você também pode usar `ThisWorkbook` para acessar o modelo de objeto do Excel. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
 Clique duas vezes o **ThisWorkbook** item de projeto no **Solution Explorer** para exibir o designer de pasta de trabalho e para exibir as propriedades e eventos da pasta de trabalho no **propriedades**janela.  
  
### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Limitações do Item de Host de pasta de trabalho no nível de documento  
 Um projeto no nível do documento pode conter apenas um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host (ou seja, a `ThisWorkbook` classe). Não é possível adicionar novos <xref:Microsoft.Office.Tools.Excel.Workbook> itens de host para seu projeto no tempo de design, e você não pode criar novos <xref:Microsoft.Office.Tools.Excel.Workbook> itens de host em tempo de execução de uma personalização no nível do documento.  
  
 Se você criar uma nova pasta de trabalho do Excel em tempo de execução, ele será do tipo <xref:Microsoft.Office.Interop.Excel.Workbook>. Porque ele não é um item de host, ele não pode conter quaisquer controles de host ou controles de formulários do Windows. Para obter mais informações sobre como criar pastas de trabalho em tempo de execução, consulte [como: programaticamente criar novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
 O <xref:Microsoft.Office.Tools.Excel.Workbook> item de host não agir como um contêiner para controles de host. Portanto, você não pode adicionar os controles visíveis para a pasta de trabalho, mas você pode adicionar componentes, como um <xref:System.Data.DataSet>, de modo que os componentes podem ser compartilhados por todas as planilhas. Em um projeto de nível de documento, os componentes disponíveis para a pasta de trabalho podem ser encontrados no **componente** guia **dados** guia e **todos os Windows Forms** guia do  **Caixa de ferramentas**.  
  
> [!NOTE]  
>  As ferramentas de desenvolvimento do Office no Visual Studio não dão suporte a pastas de trabalho compartilhadas.  
  
## <a name="understanding-workbook-host-items-in-vsto-add-in-projects"></a>Noções básicas sobre itens de Host de pasta de trabalho em projetos de suplemento do VSTO  
 Em projetos de suplemento do VSTO, você pode gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host em tempo de execução para qualquer pasta de trabalho que está aberto no Excel. Para gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host, use o método GetVstoObject. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Consulte também  
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Item de Host de planilha](../vsto/worksheet-host-item.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  