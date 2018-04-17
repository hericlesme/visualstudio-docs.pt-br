---
title: 'Como: redimensionar controles de indicador | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f740f1a56842107dff010872e532bbfc9baeec7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-bookmark-controls"></a>Como redimensionar controles de indicador
  Definir o tamanho de um <xref:Microsoft.Office.Tools.Word.Bookmark> controle quando você adiciona a um documento do Microsoft Office Word. Você também pode redimensioná-la mais tarde.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Há três maneiras de redimensionar um indicador:  
  
-   Adicionar ou remover o texto de <xref:Microsoft.Office.Tools.Word.Bookmark> controle.  
  
     Sempre que você adicionar o texto em um indicador, o tamanho do indicador automaticamente aumenta para conter o novo texto. Quando você exclui o texto, diminui o tamanho do indicador automaticamente.  
  
-   Alterar o <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> propriedades do <xref:Microsoft.Office.Tools.Word.Bookmark> controle.  
  
     Isso é útil se você estiver alterando o tamanho por apenas alguns caracteres.  
  
-   Recrie o <xref:Microsoft.Office.Tools.Word.Bookmark> controle.  
  
     Isso é útil se houver uma alteração significativa no tamanho ou local de um indicador.  
  
 Em projetos de nível de documento, você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles para o documento em seu projeto em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles para qualquer documento aberto em tempo de execução. Para obter mais informações, consulte [como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="changing-the-start-and-end-properties"></a>Alterando o início e término propriedades  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Para redimensionar um indicador em um projeto no nível do documento em tempo de design  
  
1.  Selecione o indicador de **propriedades** janela.  
  
2.  Aumente ou diminua o valor da <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> propriedade.  
  
3.  Aumente ou diminua o valor da <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> propriedade.  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Para redimensionar um indicador em um projeto no nível do documento em tempo de execução  
  
1.  Modificar o <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> propriedades de um <xref:Microsoft.Office.Tools.Word.Bookmark> criado em tempo de execução ou em tempo de design.  
  
     O exemplo de código a seguir adiciona cinco caracteres para o início de um indicador chamado `SampleBookmark`. Esse código supõe que há no mínimo cinco caracteres de texto antes do indicador.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     O exemplo de código a seguir adiciona cinco caracteres ao final do mesmo indicador. Esse código supõe que há no mínimo cinco caracteres de texto depois do indicador.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
#### <a name="to-resize-a-bookmark-in-an-vsto-add-in-project-at-run-time"></a>Para redimensionar um indicador em um projeto de suplemento do VSTO em tempo de execução  
  
1.  Modificar o <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> propriedades de um <xref:Microsoft.Office.Tools.Word.Bookmark> criado em tempo de execução.  
  
     O exemplo de código a seguir cria um <xref:Microsoft.Office.Tools.Word.Bookmark> que contém o texto do primeiro parágrafo do documento ativo e, em seguida, remove cinco caracteres de início e de término do <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreating-the-bookmark"></a>Recriando o indicador  
 Você pode redimensionar um indicador em um projeto no nível do documento adicionando um novo indicador que tem o mesmo nome que o indicador existente, mas que tem um tamanho diferente.  
  
#### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Para recriar um indicador em um projeto no nível do documento em tempo de design  
  
1.  Selecione o texto a ser incluído no novo <xref:Microsoft.Office.Tools.Word.Bookmark> controle.  
  
2.  Sobre o **inserir** menu, clique em **indicador**.  
  
3.  No **indicador** caixa de diálogo, selecione o nome do indicador que você deseja redimensionar e clique em **adicionar**.  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Como: redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Como: redimensionar controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  