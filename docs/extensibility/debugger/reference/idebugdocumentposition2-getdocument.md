---
title: IDebugDocumentPosition2::GetDocument | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentPosition2::GetDocument
helpviewer_keywords: IDebugDocumentPosition2::GetDocument
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad743a355e79d455115f31e22f1aef3dbf505992
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentposition2getdocument"></a>IDebugDocumentPosition2::GetDocument
Obtém o que contém o documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDocument(   
   IDebugDocument2** ppDoc  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppDoc`  
 [out] Retorna um [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objeto que representa o documento que contém essa posição.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)