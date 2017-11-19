---
title: Item de Host de documento | Microsoft Docs
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
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de243ee4b36d180b93e1b64f2a08c013a05d5360
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="document-host-item"></a>Item de host do documento
  O <xref:Microsoft.Office.Tools.Word.Document> item de host é um tipo que estende o <xref:Microsoft.Office.Interop.Word.Document> tipo do assembly de interoperabilidade primária para o Word. O <xref:Microsoft.Office.Tools.Word.Document> item de host fornece todas as mesmas propriedades, métodos e eventos como um <xref:Microsoft.Office.Interop.Word.Document> objeto, mas ele também expõe eventos adicionais e atua como um contêiner para controles de host e controles de formulários do Windows.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Em projetos de nível de documento, há um padrão <xref:Microsoft.Office.Tools.Word.Document> item de host que representa o documento em seu projeto. Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Word.Document> itens de host em tempo de execução.  
  
## <a name="understanding-the-document-host-item-in-document-level-projects"></a>Noções básicas sobre o Item de Host do documento em projetos no nível de documento  
 Para acessar o documento em seu projeto, use o `ThisDocument` classe. Quando você cria um projeto no nível do documento, o Visual Studio gera o `ThisDocument` classe para servir como o link de comunicação entre o Word e o código de personalização. O `ThisDocument` classe fornece acesso a membros de <xref:Microsoft.Office.Tools.Word.Document> item de host para executar tarefas básicas em sua personalização, como executar código quando o documento for aberto ou fechado. Você também pode usar a classe para adicionar controles ao documento. Combinando conjuntos diferentes de controles e escrever código, que você pode vincular os controles a dados, coletar informações do usuário e responder a ações do usuário. Para obter mais informações, consulte [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
 O `ThisDocument` classe fornece um local no qual começar a gravar código no seu projeto. Porque a classe fornece todas as mesmas propriedades, métodos e eventos como o <xref:Microsoft.Office.Interop.Word.Document> do objeto no assembly de interoperabilidade primário para o Word, você também pode usar `ThisDocument` para acessar o modelo de objeto do Word. Para obter mais informações, consulte [visão geral de modelo de objeto do Word](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Limitações do Item de Host do documento em projetos no nível de documento  
 Um projeto no nível do documento pode conter apenas um <xref:Microsoft.Office.Tools.Word.Document> item de host (ou seja, a `ThisDocument` classe). Não é possível adicionar novos <xref:Microsoft.Office.Tools.Word.Document> itens de host para seu projeto no tempo de design, e você não pode criar novos <xref:Microsoft.Office.Tools.Word.Document> itens de host em tempo de execução de uma personalização no nível do documento.  
  
 Se você criar um novo documento do Word em tempo de execução, ele será do tipo <xref:Microsoft.Office.Interop.Word.Document>. Porque ele não é um item de host, ele não pode conter quaisquer controles de host ou controles de formulários do Windows. Para obter mais informações sobre a criação de documentos em tempo de execução, consulte [como: criar novos documentos programaticamente](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understanding-document-host-items-in-application-level-projects"></a>Noções básicas sobre itens de Host de documento em projetos no nível de aplicativo  
 Em projetos de suplemento do VSTO, você pode gerar um <xref:Microsoft.Office.Tools.Word.Document> item de host em tempo de execução para qualquer documento que está aberto no Word. Você pode usar o <xref:Microsoft.Office.Tools.Word.Document> item de host para adicionar controles para o documento associado ou manipular eventos que não estão disponíveis em <xref:Microsoft.Office.Interop.Word.Document> objetos.  
  
 Para gerar um <xref:Microsoft.Office.Tools.Word.Document> item de host, use o método GetVstoObject. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Consulte também  
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO no tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  