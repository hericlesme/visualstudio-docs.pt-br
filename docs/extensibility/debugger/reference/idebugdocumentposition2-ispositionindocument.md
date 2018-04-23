---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 225a92d521f118c2d038cabf114c69f389af0108
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Determina se a posição do documento está contida em um determinado documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDoc`  
 [in] O [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objeto que representa o candidato de documento que contém.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado principalmente em Configurar pontos de interrupção [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaces. Como documentos são carregados, a posição do ponto de interrupção é chamada para determinar se o documento contém nessa posição.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)