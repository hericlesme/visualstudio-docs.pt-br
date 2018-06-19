---
title: Automatizar o Word usando objetos estendidos
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ac9c610cdc7111eaeb5204e1b9d4fe6cde27a9c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264854"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatizar o Word usando objetos estendidos
  Ao desenvolver soluções do Word no Visual Studio, você pode usar *itens de host* e *controle de host*s em suas soluções. Esses são objetos que estendem determinados objetos usados no modelo de objeto do Word (ou seja, o modelo de objeto que é exposto pelo assembly de interoperabilidade primária para o Word), como o <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl> objetos. Os objetos estendidos se comportam como os objetos do Word que eles se baseiam, mas adicionar eventos adicionais e recursos de associação de dados para os objetos.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Itens de host e controles de host estão disponíveis em suplementos do VSTO e personalizações no nível do documento, embora o contexto no qual eles podem ser usados é diferente para cada tipo de solução. Para obter mais informações, consulte [itens de Host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Item de host do documento  
 Palavras fornecem projetos acesso a <xref:Microsoft.Office.Tools.Word.Document> item de host. O <xref:Microsoft.Office.Tools.Word.Document> item de host atua como um contêiner para outros controles, incluindo controles de host e controles de formulários do Windows, e mantém informações sobre os controles em sua superfície. O <xref:Microsoft.Office.Tools.Word.Document> item de host também fornece a maioria dos mesmos membros como o <xref:Microsoft.Office.Interop.Word.Document> classe, que é a classe correspondente no modelo de objeto do Word.  
  
 Para obter mais informações, consulte [item de host do documento](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>controles de host do Word  
 Há vários controles de host para o Word que ajudarão a criar, organizar e automatizar documentos. A maioria das suas funcionalidades envolve a importação, apresentando e proteção de dados. Esses controles de host fornecem eventos e os recursos de associação de dados que não têm contrapartes no modelo de objeto do Word nativo.  
  
 Em projetos de nível de documento, você pode adicionar qualquer controle de host para o documento em tempo de design, ou você pode adicionar controles de conteúdo e controles de indicador em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar controles de conteúdo e controles de indicador para qualquer documento aberto em tempo de execução.  
  
 Para obter mais informações sobre os controles de host, que você pode usar em projetos do Word, consulte os tópicos a seguir:  
  
-   [Controles de conteúdo](../vsto/content-controls.md)  
  
-   [Controle indicador](../vsto/bookmark-control.md)  
  
-   [Controle XMLNode](../vsto/xmlnode-control.md)  
  
-   [Controle XMLNodes](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar controles content a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Como: adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Como: adicionar controles XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Como: redimensionar controles de indicador](../vsto/how-to-resize-bookmark-controls.md)   
 [Passo a passo: Criar um modelo usando os controles de conteúdo](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Passo a passo: Associar controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Passo a passo: Criar menus de atalho para indicadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Soluções do Word](../vsto/word-solutions.md)   
 [Itens de host e visão geral dos controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Estender a documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  