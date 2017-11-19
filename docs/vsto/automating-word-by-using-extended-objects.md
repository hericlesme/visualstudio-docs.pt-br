---
title: Automatizando o Word usando objetos estendidos | Microsoft Docs
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
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
ms.assetid: 3911c7cd-7092-468d-bd82-2fdec53a2d9b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: efcd5ec4da94e1e3441ffbecafeeb54e1f896bd9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="automating-word-by-using-extended-objects"></a>Automatizando o Word usando objetos estendidos
  Ao desenvolver soluções do Word no Visual Studio, você pode usar *itens de host* e *controle de host*s em suas soluções. Esses são objetos que estendem determinados objetos usados no modelo de objeto do Word (ou seja, o modelo de objeto que é exposto pelo assembly de interoperabilidade primária para o Word), como o <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl> objetos. Os objetos estendidos se comportam como os objetos do Word que eles se baseiam, mas adicionar eventos adicionais e recursos de associação de dados para os objetos.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Itens de host e controles de host estão disponíveis em suplementos do VSTO e personalizações no nível do documento, embora o contexto no qual eles podem ser usados é diferente para cada tipo de solução. Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Item de host do documento  
 Palavras fornecem projetos acesso a <xref:Microsoft.Office.Tools.Word.Document> item de host. O <xref:Microsoft.Office.Tools.Word.Document> item de host atua como um contêiner para outros controles, incluindo controles de host e controles de formulários do Windows, e mantém informações sobre os controles em sua superfície. O <xref:Microsoft.Office.Tools.Word.Document> item de host também fornece a maioria dos mesmos membros como o <xref:Microsoft.Office.Interop.Word.Document> classe, que é a classe correspondente no modelo de objeto do Word.  
  
 Para obter mais informações, consulte [Item de Host do documento](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>Controles de Host do Word  
 Há vários controles de host para o Word que ajudarão a criar, organizar e automatizar documentos. A maioria das suas funcionalidades envolve a importação, apresentando e proteção de dados. Esses controles de host fornecem eventos e os recursos de associação de dados que não têm contrapartes no modelo de objeto do Word nativo.  
  
 Em projetos de nível de documento, você pode adicionar qualquer controle de host para o documento em tempo de design, ou você pode adicionar controles de conteúdo e controles de indicador em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar controles de conteúdo e controles de indicador para qualquer documento aberto em tempo de execução.  
  
 Para obter mais informações sobre os controles de host, que você pode usar em projetos do Word, consulte os tópicos a seguir:  
  
-   [Controles de conteúdo](../vsto/content-controls.md)  
  
-   [Controle do Indicador](../vsto/bookmark-control.md)  
  
-   [Controle do XMLNode](../vsto/xmlnode-control.md)  
  
-   [Controle do XMLNodes](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar controles Content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Como: adicionar controles XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Como: redimensionar controles de indicador](../vsto/how-to-resize-bookmark-controls.md)   
 [Passo a passo: Criando um modelo usando os controles de conteúdo](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Passo a passo: Associando controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Passo a passo: Criando Menus de atalho para indicadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Soluções do Word](../vsto/word-solutions.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO no tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  