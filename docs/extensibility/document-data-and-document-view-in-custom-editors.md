---
title: "Dados de documento e documento de exibição em editores personalizados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab3506a6906c4223888a14132339cbe5499c92d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dados de documento e visualização de documentos em editores personalizados
Um editor personalizado consiste em duas partes: um objeto de dados de documento e um objeto de exibição do documento. Como os nomes sugerem, o objeto de dados de documento representa os dados de texto a ser exibida e o objeto de exibição de documento (ou "view") representa uma ou mais janelas no qual exibir o objeto de dados de documento.  
  
## <a name="document-data-object"></a>Objeto de dados de documento  
 Um objeto de dados de documento é uma representação de dados de texto no buffer de texto. É um objeto COM que armazena o texto do documento e outras informações, manipula a persistência de documento e permite que vários modos de exibição de seus dados. Para saber mais, veja  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>e [documento Windows](../extensibility/internals/document-windows.md).  
  
 Designers e editores personalizados podem optar por usar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> seu próprios buffer personalizado ou objeto. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>segue o modelo de incorporação simplificado para um editor padrão, dá suporte a vários modos de exibição e fornece interfaces de evento que são usados para gerenciar vários modos de exibição.  
  
## <a name="document-view-object"></a>Objeto de exibição de documento  
 Uma janela que exibe o código e outro texto é conhecida como um documento do modo de exibição ou exibição. Quando você cria um editor, você pode escolher uma única visualização, no qual o texto é exibido em uma única janela, ou uma exibição de várias, no qual o texto é exibido em mais de uma janela. Sua escolha depende de seu aplicativo. Por exemplo, se você precisar de uma edição lado a lado, escolha exibir vários. Cada exibição é associada uma entrada no ambiente de desenvolvimento integrado do (IDE) a tabela de documento (RDT) em execução. Windows de modo de exibição pertencem a um projeto ou um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto.  
  
 Se o editor oferece suporte a vários modos de exibição de um objeto de dados de documento, em seguida, seus dados de documento e objetos de exibição de documento devem ser separados. Caso contrário, eles podem ser agrupados. Para obter mais informações, consulte [dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
 O IDE notifica exibições sobre eventos (por exemplo, quando uma solução que contém um documento é fechada) correspondendo um identificador de item (ItemID) para cada entrada na tabela de documento em execução. Para obter mais informações sobre isso, consulte [tabela de documento executando](../extensibility/internals/running-document-table.md).  
  
 Há duas opções para criar um modo de exibição para um editor personalizado. Um é o modelo de ativação no local, em que a exibição é hospedada em uma janela usando um controle ActiveX ou um objeto de dados de documento. O segundo é o modelo de incorporação simplificado, em que a exibição é hospedada por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> é implementado para lidar com os comandos de janela. Para obter informações sobre o modelo de ativação no local, consulte [ativação no local](../extensibility/in-place-activation.md). Para obter informações sobre o modelo de incorporação simplificado, consulte [inserindo simplificado](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Consulte também  
 [Dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md)   
 [Simplificado inserindo](../extensibility/simplified-embedding.md)   
 [Como: anexar modos de exibição para dados de documento](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gerenciamento de proprietário de bloqueio de documentos](../extensibility/document-lock-holder-management.md)   
 [Modos de exibição único e multi-guia](../extensibility/single-and-multi-tab-views.md)   
 [Salvar um documento padrão](../extensibility/internals/saving-a-standard-document.md)   
 [A tabela de documentos em execução e persistência](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinando que Editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fábricas de editor](../extensibility/editor-factories.md)