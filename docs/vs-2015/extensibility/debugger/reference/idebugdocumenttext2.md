---
title: IDebugDocumentText2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7856512e4dc8b5bb7dfe82c82ce51af23d3959a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464867"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugDocumentText2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumenttext2).  
  
Essa interface representa um documento de texto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um mecanismo de depuração (DES) implementa essa interface quando ele precisa fornecer o código-fonte está na forma de texto. Como esse é o caso mais comum, se a DE implementa o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface, ele deve implementar também a `IDebugDocumentText2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use o `QueryInterface` método para obter essa interface de um `IDebugDocument2` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos no `IDebugDocument2` interface, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera o tamanho do texto nessa posição no documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera o texto da posição especificada no documento.|  
  
## <a name="remarks"></a>Comentários  
 Um objeto que implementa essa interface deve implementar também a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> da interface, que fornece a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface para um [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

