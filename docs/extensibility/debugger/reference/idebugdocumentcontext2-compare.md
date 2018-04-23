---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f41b0e5973af8e0cb65f093f51137059084c9792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento para uma determinada matriz de contextos de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `compare`  
 [in] Um valor da [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumeração que especifica o tipo de comparação.  
  
 `rgpDocContextSet`  
 [in] Uma matriz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que representam os contextos de documento que estão sendo comparados para.  
  
 `dwDocContextSetLen`  
 [in] O comprimento da matriz de contextos de documento a ser comparado.  
  
 `pdwDocContext`  
 [out] Retorna o índice de `rgpDocContextSet` matriz do contexto do documento primeiro que satisfaz a comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se uma correspondência foi encontrada. Retorna `S_FALSE` se nenhuma correspondência foi encontrada. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que são passados na matriz devem ser implementados pelo mecanismo de depuração mesmo que implementa o `IDebugDocumentContext2` do objeto que está sendo chamado; caso contrário, a comparação não é válida.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)