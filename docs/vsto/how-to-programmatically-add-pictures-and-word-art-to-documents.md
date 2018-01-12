---
title: 'Como: adicionar programaticamente imagens e Word Art a documentos | Microsoft Docs'
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
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 84917f3f472529bd46463a1f7cecf83c2e9185ac
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Como adicionar imagens e Word Art a documentos programaticamente
  Você pode adicionar imagens e objetos de desenho para seus documentos em tempo de design ou em tempo de execução. WordArt permite que você adicione texto decorativo para documentos do Microsoft Office Word. Esses efeitos especiais de texto são objetos que você pode personalizar e inserir no documento de desenho.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="adding-a-picture-at-design-time"></a>Adicionando uma imagem em tempo de Design  
 Se você estiver desenvolvendo uma personalização no nível do documento, você pode adicionar uma imagem para o documento em tempo de design.  
  
#### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Para adicionar uma imagem a um documento do Word em tempo de design  
  
1.  Coloque o cursor onde você deseja inserir a imagem no documento.  
  
2.  Clique o **inserir** guia da faixa de opções.  
  
3.  No **ilustrações** de grupo, clique em **imagem**.  
  
4.  No **Inserir imagem** caixa de diálogo, navegue até a imagem que você deseja inserir e clique em **inserir**.  
  
     A imagem é adicionada ao documento na posição atual do cursor.  
  
## <a name="adding-a-picture-at-run-time"></a>Adicionar uma imagem em tempo de execução  
 Você pode inserir uma imagem em um documento no local atual do cursor.  
  
#### <a name="to-add-a-picture-at-the-cursor-location"></a>Para adicionar uma imagem no local do cursor  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> método o <xref:Microsoft.Office.Interop.Word.InlineShapes> coleta e passar no nome do arquivo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="adding-wordart-at-design-time"></a>Adicionando WordArt em tempo de Design  
 Se você estiver desenvolvendo uma personalização no nível do documento, você pode adicionar WordArt o documento em tempo de design.  
  
#### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Para adicionar WordArt a um documento do Word em tempo de design  
  
1.  Coloque o cursor onde você deseja inserir o WordArt no documento.  
  
2.  Clique o **inserir** guia da faixa de opções.  
  
3.  No **texto** de grupo, clique em **WordArt**e, em seguida, selecione um estilo de WordArt.  
  
4.  Adicione o texto que você deseja exibir no documento para o **editar texto da WordArt** caixa de diálogo e clique em **Okey**.  
  
     O texto é adicionado ao documento com o estilo de WordArt selecionado aplicado.  
  
## <a name="adding-wordart-at-run-time"></a>Adicionando WordArt em tempo de execução  
 Você pode inserir WordArt em um documento no local atual do cursor. O procedimento é diferente para personalizações no nível do documento e suplementos do VSTO.  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Para adicionar WordArt na posição do cursor em uma personalização no nível do documento  
  
1.  Obtenha a posição esquerda e superior do local atual do cursor.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Chamar o <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> método o <xref:Microsoft.Office.Interop.Word.Shapes> objeto do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Para adicionar WordArt na posição do cursor em um suplemento do VSTO  
  
1.  Obtenha a posição esquerda e superior do local atual do cursor.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Chamar o <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> método o <xref:Microsoft.Office.Interop.Word.Shapes> objeto do documento ativo (ou outro documento que você especificar).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Uma imagem chamada **SamplePicture.jpg** devem existir na unidade C.  
  
## <a name="see-also"></a>Consulte também  
 [Como: abrir documentos existentes programaticamente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Como: programaticamente inserir texto em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Como: programaticamente restaurar seleções após pesquisas](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Como: salvar documentos programaticamente](../vsto/how-to-programmatically-save-documents.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  