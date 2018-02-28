---
title: Objeto VSTextBuffer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 643bd434e058a24cc17936d9ab2f333489b8aa5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="vstextbuffer-object"></a>Objeto VSTextBuffer
O objeto de buffer de texto representa um fluxo de texto Unicode, que é geralmente associado um arquivo. Um <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto pode ser usado fora do contexto do editor de núcleo, como no caso de um assistente.  
  
 A tabela a seguir mostra as interfaces de `VSTextBuffer`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interface OLE padrão. Usado principalmente para tratamento no buffer de desfazer/refazer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interface OLE padrão.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações de compostos (ou seja, ações que são agrupadas em uma unidade de desfazer/refazer único).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita a persistência de dados de documento gerenciados pelo buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Usado para pesquisar um buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece leitura e gravação de recursos usando as coordenadas bidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece leitura e gravação de recursos usando coordenadas unidimensionais. Herda de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápida, fornece acesso sequencial orientado por fluxo de texto no buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome ou identificador de origem do buffer. Você pode armazenar seus próprios dados aleatórios no buffer com esta interface por criar um GUID e usá-lo como uma chave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Oferece suporte a pontos de conexão para eventos.|  
  
## <a name="remarks"></a>Comentários  
 O `VSTextBuffer` geralmente são encontrados por um `QueryInterface` chamar `IVsTextBuffer`. Para obter mais informações, consulte [Buffer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edição de figuras](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)