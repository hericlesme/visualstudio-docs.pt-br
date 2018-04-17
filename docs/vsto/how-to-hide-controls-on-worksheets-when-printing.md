---
title: 'Como: ocultar controles em planilhas ao imprimir | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d02d823e707054fd17a5f3f892db41258b08081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Como ocultar controles em planilhas durante a impressão
  Quando você imprime um documento do Microsoft Office Excel que contém os controles de formulários do Windows, os controles são visíveis na planilha impressa. Você pode ocultar os controles ao imprimir uma planilha.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Se você ocultar os controles que exibem dados, como um <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, os dados no controle não serão visíveis na planilha impressa.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar os controles quando uma planilha é impressa  
  
1.  Criar ou abrir um projeto do Excel no Visual Studio e verifique **Planilha1** está visível no designer. Para obter informações sobre a criação de projetos, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Do **controles comuns** guia do **caixa de ferramentas**, arraste um <xref:Microsoft.Office.Tools.Excel.Controls.Button> control para uma célula em `Sheet1`.  
  
3.  No **propriedades** janela, defina o <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propriedade **False**.  
  
## <a name="see-also"></a>Consulte também  
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controles em Visão geral de documentos do Office do Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Como: adicionar controles a documentos do Office do Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Como redimensionar controles dentro de células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  