---
title: Objeto VSTextView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5be89d01a668fd05e70e73e31ffaf3742317c272
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138721"
---
# <a name="vstextview-object"></a>Objeto VSTextView
A exibição de texto é uma janela que permite aos usuários exibir e editar o texto Unicode do buffer de texto. Essencialmente, o modo de exibição é que se referem a maioria dos usuários como o editor. Porque o modo de exibição é separado do buffer por várias camadas de texto (quebra automática de linha, estrutura de tópicos de texto e assim por diante), o modo de exibição não é garantido para ser uma representação exata do texto no buffer. Para obter mais informações sobre a exibição de texto, consulte [acessando theText exibição usando a API herdado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 A tabela a seguir mostra as interfaces de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações compostas (ou seja, ações que são agrupadas em uma unidade de desfazer/refazer único).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornece os métodos básicos para gerenciar e acessar o modo de exibição. `IVsTextView` não é thread safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Cria e gerencia um painel de janela.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interage com camadas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Executa operações no modo de exibição de um thread diferente.|  
  
## <a name="see-also"></a>Consulte também  
 [Edição de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Acessando theText exibição usando a API herdado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)