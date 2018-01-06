---
title: 'Como: implementar o gerenciamento de desfazer | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cf57b24d81e193294f5ab90f71af07b229ec5839
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-undo-management"></a>Como: implementar o gerenciamento de desfazer
É a principal interface usada para o gerenciamento de desfazer <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, que é implementado pelo ambiente. Para dar suporte ao gerenciamento de desfazer, implementar unidades de desfazer separado (ou seja, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, que pode conter várias etapas individuais.  
  
 Como implementar o gerenciamento de desfazer varia dependendo se o editor oferece suporte a vários modos de exibição ou não. Os procedimentos para cada implementação são detalhados nas seções a seguir.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casos onde um editor compatível com uma única exibição  
 Nesse cenário, o editor não oferece suporte a vários modos de exibição. Há apenas um editor e um documento, e dão suporte desfazer. Use o procedimento a seguir para implementar o gerenciamento de desfazer.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Para dar suporte ao gerenciamento de desfazer para um editor de modo de exibição único  
  
1.  Chamar `QueryInterface` no `IServiceProvider` interface no quadro da janela para `IOleUndoManager`, do objeto de visualização de documento para acessar o Gerenciador de desfazer (`IID_IOLEUndoManager`).  
  
2.  Quando uma exibição é localizada em um quadro de janela, obtém um ponteiro de site, ele pode usar para chamar `QueryInterface` para `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casos onde um editor compatível com várias exibições  
 Se você tiver a separação de documento e exibição, há Gerenciador de desfazer normalmente um associado com o documento em si. Todas as unidades de desfazer são colocadas no Gerenciador de um Desfazer associado ao objeto de dados de documento.  
  
 Em vez da consulta de modo de exibição para o Gerenciador de desfazer, de que há um para cada modo de exibição, os dados de documento objeto chamadas <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para instanciar o Gerenciador de desfazer, especificando um identificador de classe de CLSID_OLEUndoManager. O identificador de classe é definido no arquivo OCUNDOID.h.  
  
 Ao usar <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para criar sua própria instância do Gerenciador de desfazer, use o procedimento a seguir para conectar-se com o Gerenciador de desfazer no ambiente.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Para conectar-se com o Gerenciador de desfazer no ambiente  
  
1.  Chamar `QueryInterface` no objeto retornado de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> para `IID_IOleUndoManager`. Armazenar o ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Chamar `QueryInterface` na `IOleUndoManager` para `IID_IOleCommandTarget`. Armazenar o ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Retransmissão seu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chama armazenado `IOleCommandTarget` interface para os seguintes comandos StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Chamar `QueryInterface` na `IOleUndoManager` para `IID_IVsChangeTrackingUndoManager`. Armazenar o ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Use o ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> para chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> métodos.  
  
5.  Chamar `QueryInterface` na `IOleUndoManager` para `IID_IVsLinkCapableUndoManager`.  
  
6.  Chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> com o documento, que também deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interface. Quando o documento é fechado, chame `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Quando o documento é fechado, chame `QueryInterface` em seu Gerenciador de desfazer para `IID_IVsLifetimeControlledObject`.  
  
8.  Call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Quando forem feitas alterações no documento, chame <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> no Gerenciador de com um `OleUndoUnit` classe. O <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> método mantém uma referência ao objeto, geralmente você o soltar logo após o <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 O `OleUndoManager` classe representa uma instância de pilha de desfazer única. Portanto, há um objeto do Gerenciador de desfazer por entidade de dados que estão sendo controlada para desfazer ou refazer.  
  
> [!NOTE]
>  Enquanto o objeto do Gerenciador de desfazer é usado pelo editor de texto, ele é um componente geral que tem suporte específico para o editor de texto. Se você desejar oferecer suporte a vários nível desfazer ou refazer, você pode usar esse objeto para fazer isso.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Como: limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)