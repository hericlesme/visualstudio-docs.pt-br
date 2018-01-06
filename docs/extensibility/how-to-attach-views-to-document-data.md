---
title: "Como: anexar modos de exibição para dados de documentos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bcbb3e6b475a9dcd22d012073d3197013da337c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-views-to-document-data"></a>Como: anexar modos de exibição para dados de documento
Se você tiver um novo modo de exibição de documento, você poderá anexá-lo a um objeto de dados de documento existente.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar se você pode anexar um modo de exibição para um objeto de dados de documento existente  
  
1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  Na implementação de `IVsEditorFactory::CreateEditorInstance`, chame `QueryInterface` sobre o objeto de dados de documento existente quando o IDE chama seu `CreateEditorInstance` implementação.  
  
     Chamando `QueryInterface` permite que você examine o objeto de dados de documento existente, que é especificado no `punkDocDataExisting` parâmetro.  
  
     As interfaces exatas, você deverá consultar, no entanto, depende do editor que é abrir o documento, conforme descrito na etapa 4.  
  
3.  Se você não encontrar as interfaces apropriadas no objeto de dados de documento existente, retorne um código de erro para o seu editor indicando que o objeto de dados de documento é incompatível com seu editor.  
  
     Na implementação do IDE do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, uma caixa de mensagem avisará que o documento está aberto em outro editor e pergunta se você deseja fechá-lo.  
  
4.  Se você fechar este documento, o Visual Studio chama sua fábrica de editor para uma segunda vez. Essa chamada, o `DocDataExisting` parâmetro for igual a NULL. Sua implementação de fábrica de editor, em seguida, poderá abrir o objeto de dados de documento em seu próprio editor.  
  
    > [!NOTE]
    >  Para determinar se você pode trabalhar com um objeto de dados de documento existente, você também pode usar privado Conhecimento da implementação da interface convertendo um ponteiro para o valor real [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe de implementação privada. Por exemplo, implementam todos os editores padrão `IVsPersistFileFormat`, que herda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Assim, você pode chamar `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, e se a ID de classe no objeto de dados de documento existente corresponde a sua implementação de ID de classe, em seguida, você pode trabalhar com o objeto de dados de documento.  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando o Visual Studio chama sua implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, ele passa novamente um ponteiro para o objeto de dados de documento existente no `punkDocDataExisting` parâmetro, se houver. Examine o objeto de dados de documento retornado no `punkDocDataExisting` para determinar se o objeto de dados de documento é apropriado para seu editor conforme descrito na observação na etapa 4 do procedimento neste tópico. Se for apropriado, sua fábrica de editor deve fornecer um segundo modo de exibição para os dados, conforme descrito na [dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md). Caso contrário, em seguida, ele deve exibir uma mensagem de erro apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Dando suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md)   
 [Dados de documentos e exibição de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)