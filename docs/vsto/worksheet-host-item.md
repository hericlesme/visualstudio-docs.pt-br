---
title: Item de Host de planilha | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c89fa79a73393afa2919554de790c307b2ea68b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="worksheet-host-item"></a>Item de host da planilha
  O <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host é um tipo que estende o <xref:Microsoft.Office.Interop.Excel.Worksheet> tipo do assembly de interoperabilidade primária para o Excel. O <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host fornece todas as mesmas propriedades, métodos e eventos como um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto, mas ele também expõe eventos adicionais e atua como um contêiner para controles de host e controles de formulários do Windows.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Em projetos de nível de documento, você pode adicionar <xref:Microsoft.Office.Tools.Excel.Worksheet> hospedar itens ao seu projeto em tempo de design. Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host em tempo de execução.  
  
## <a name="understanding-worksheet-host-items-in-document-level-projects"></a>Noções básicas sobre itens de Host de planilha em projetos no nível de documento  
 Quando você cria um projeto de nível de documento para Excel, o Visual Studio cria automaticamente três <xref:Microsoft.Office.Tools.Excel.Worksheet> hospedar itens no projeto. Os nomes padrão das planilhas são `Sheet1`, `Sheet2`, e `Sheet3`. Se você criar um projeto com base em uma pasta de trabalho, o número de itens de host depende do número de planilhas na pasta de trabalho.  
  
 Essas classes de planilha lhe dará acesso a membros do <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host para executar tarefas básicas em sua personalização, como modificar o conteúdo de uma planilha. Você também pode usar essas classes para adicionar controles a planilhas. Combinando conjuntos diferentes de controles e escrever código, que você pode vincular os controles a dados, coletar informações do usuário e responder a ações do usuário. Para obter mais informações, consulte [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
 As classes de planilha fornecem um local no qual começar a gravar código no seu projeto. Porque a classe fornece todas as mesmas propriedades, métodos e eventos como a <xref:Microsoft.Office.Interop.Excel.Worksheet> do objeto no assembly de interoperabilidade primário para o Excel, você também pode usar essas classes para acessar o modelo de objeto do Excel. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
 Em projetos de nível de documento, você pode adicionar mais <xref:Microsoft.Office.Tools.Excel.Worksheet> itens para o projeto de host em tempo de design, adicionando uma nova planilha na pasta de trabalho no designer.  
  
### <a name="renaming-worksheets"></a>Renomeando planilhas  
 Em um projeto de nível de documento, você pode renomear as planilhas no designer do Visual Studio, mas isso altera o nome de exibição da planilha. O nome programático ainda é o nome padrão da planilha. Se você renomear a planilha no **propriedades** janela, apenas o nome programático é alterada.  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Limitações do Item de Host de planilha em projetos no nível de documento  
 Você não pode criar novos <xref:Microsoft.Office.Tools.Excel.Worksheet> itens de host em tempo de execução em um projeto no nível do documento. Se você criar uma nova planilha do Excel em tempo de execução, ele será do tipo <xref:Microsoft.Office.Interop.Excel.Worksheet>. Porque ele não é um item de host, ele não pode conter quaisquer controles de host ou controles de formulários do Windows. Para obter mais informações sobre a criação de documentos em tempo de execução, consulte [como: programaticamente adicionar novas planilhas a pastas de trabalho](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## <a name="understanding-worksheet-host-items-in-vsto-add-in-projects"></a>Noções básicas sobre itens de Host de planilha em projetos de suplemento do VSTO  
 Em projetos de nível de aplicativo, você pode gerar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host em tempo de execução para qualquer planilha que está aberto no Excel. Você pode usar o <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host para adicionar controles à planilha associada, ou para manipular eventos que não estão disponíveis em <xref:Microsoft.Office.Interop.Excel.Worksheet> objetos.  
  
 Para gerar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host, use o método GetVstoObject. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Consulte também  
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Item de Host de pasta de trabalho](../vsto/workbook-host-item.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  