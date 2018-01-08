---
title: 'Como: mapear esquemas para planilhas dentro do Visual Studio | Microsoft Docs'
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2dc089fb2c4ae2714a0b94d7756aaa432406ef74
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Como mapear esquemas para planilhas dentro do Visual Studio
  Você pode mapear um esquema XML para uma planilha, enquanto a planilha está aberta no Visual Studio. Você usar as mesmas ferramentas do Microsoft Office Excel que você usa quando a pasta de trabalho é aberta fora do Visual Studio. O Office project cria os objetos de mesmo se você mapear o esquema para a planilha antes ou depois de criar sua solução do Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Você não pode usar os esquemas XML com diversas partes em soluções do Excel.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Para mapear um esquema XML para uma planilha do Excel no Visual Studio  
  
1.  Abra o projeto de modelo ou pasta de trabalho do Excel dentro do Visual Studio.  
  
2.  Clique na planilha para mover o foco para o designer.  
  
3.  Na faixa de opções, clique no **desenvolvedor** guia.  
  
    > [!NOTE]  
    >  Se o **desenvolvedor** guia não estiver visível, você deve primeiro mostrá-la. Para obter mais informações, consulte [como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  No **XML** de grupo, clique em **fonte**.  
  
     O **origem XML** janela será aberta.  
  
5.  No **origem XML** janela, clique em **mapas XML**.  
  
     O **mapas XML** caixa de diálogo é aberta.  
  
6.  No **mapas XML** caixa de diálogo, clique em **adicionar**.  
  
7.  Navegue até seu arquivo de esquema, selecione-o e, em seguida, clique em **abrir**.  
  
8.  Clique em **OK**.  
  
     O esquema é representado no **origem XML** janela. No seu projeto, com um tipo <xref:System.Data.DataSet> é gerado com base no esquema e um <xref:System.Windows.Forms.BindingSource> é criado.  
  
9. Arraste elementos do **origem XML** janela para os locais na planilha em que você deseja que os controles correspondentes a ser criado.  
  
     Se você arrastar um elemento de esquema não repetitivo, o projeto do Office gera um <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controle associado automaticamente para o <xref:System.Windows.Forms.BindingSource>.  
  
     Se você arrastar um elemento de esquema repetido, o projeto do Office gera um <xref:Microsoft.Office.Tools.Excel.ListObject> controle que não esteja associado a uma fonte de dados automaticamente. Para obter mais informações, consulte [esquemas XML e dados em personalizações no nível do documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: mapear esquemas para documentos do Word dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Esquemas e dados XML em personalizações no nível do documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  