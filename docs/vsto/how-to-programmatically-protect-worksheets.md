---
title: 'Como: proteger planilhas programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 23e0706f7436355e2308fbde8d945968da5348c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-protect-worksheets"></a>Como proteger planilhas programaticamente
  O recurso de proteção do Microsoft Office Excel ajuda a impedir que os usuários e o código modificar objetos em uma planilha. Por padrão, todas as células são bloqueadas após você ativar a proteção.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Em personalizações no nível do documento, você pode proteger planilhas usando o designer do Excel. Você também pode proteger uma planilha programaticamente no tempo de execução em qualquer tipo de projeto.  
  
> [!NOTE]  
>  Você não pode adicionar controles de formulários do Windows para áreas de uma planilha que estão protegidas.  
  
## <a name="using-the-designer"></a>Usando o Designer  
  
#### <a name="to-protect-a-worksheet-in-the-designer"></a>Para proteger uma planilha no designer  
  
1.  No **alterações** grupo de **revisão** , clique em **Proteger planilha**.  
  
     O **Proteger planilha** caixa de diálogo é exibida. Você pode definir uma senha e, opcionalmente, especificar determinadas ações que os usuários têm permissão para executar com a planilha, como formatar células ou inserir linhas.  
  
 Você também pode permitir que os usuários editem intervalos específicos em planilhas protegidas.  
  
#### <a name="to-allow-editing-in-specific-ranges"></a>Para permitir a edição em intervalos específicos  
  
1.  No **alterações** grupo de **revisão** , clique em **permitem que os usuários editem intervalos**.  
  
     O **permitem que os usuários editem intervalos** caixa de diálogo é exibida. Você pode especificar intervalos sejam desbloqueados usando uma senha e usuários que podem editar intervalos sem uma senha.  
  
## <a name="using-code-at-run-time"></a>Usando o código em tempo de execução  
 O código a seguir define a senha (usando a variável getPasswordFromUser, que contém uma senha obtida do usuário) e permite classificar somente.  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Para proteger uma planilha usando código em uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> método da planilha. Este exemplo presume que você está trabalhando com uma planilha denominada `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Para proteger uma planilha usando código em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> método da planilha ativa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: remover proteção de planilhas programaticamente](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Como: programaticamente proteger pastas de trabalho](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Item de Host de planilha](../vsto/worksheet-host-item.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  