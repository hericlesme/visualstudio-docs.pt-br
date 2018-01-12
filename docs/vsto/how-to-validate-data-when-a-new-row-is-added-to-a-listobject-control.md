---
title: "Como: validar dados quando uma nova linha é adicionada a um controle ListObject | Microsoft Docs"
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
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 509d298dc3ac10a91f2eb10aa8bcb26a9738f4d4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Como validar dados quando uma nova linha é adicionada a um controle ListObject
  Os usuários podem adicionar novas linhas para um <xref:Microsoft.Office.Tools.Excel.ListObject> controle associado a dados. Você pode validar os dados do usuário antes de confirmar as alterações para a fonte de dados.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Validação de dados  
 Sempre que uma linha é adicionada a um <xref:Microsoft.Office.Tools.Excel.ListObject> que está associado a dados, o <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> é gerado. Você pode manipular esse evento para executar a validação de dados. Por exemplo, se seu aplicativo exigir que somente os funcionários entre a idade de 18 e 65 podem ser adicionados à fonte de dados, você pode verificar a idade inserida cai dentro desse intervalo antes que a linha é adicionada.  
  
> [!NOTE]  
>  Sempre verifique a entrada do usuário no servidor, além de cliente. Para obter mais informações, consulte [proteger aplicativos de cliente](/dotnet/framework/data/adonet/secure-client-applications).  
  
#### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Para validar dados quando uma nova linha é adicionada à associação de dados ListObject  
  
1.  Criar variáveis para a ID e <xref:System.Data.DataTable> no nível de classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Criar um novo <xref:System.Data.DataTable> e adicionar colunas de exemplo e os dados no `Startup` manipulador de eventos do `Sheet1` classe (em um projeto no nível de documento) ou `ThisAddIn` classe (em um projeto de suplemento do VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Adicione código para o `list1_BeforeAddDataBoundRow` manipulador de eventos para verificar se a idade inserida está dentro do intervalo aceitável.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código pressupõe que você tiver uma <xref:Microsoft.Office.Tools.Excel.ListObject> chamado `list1` na planilha em que esse código é exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Controle ListObject](../vsto/listobject-control.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Como mapear colunas ListObject para dados](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  