---
title: IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03fbc1499372221a815eb639442af586f7020cf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100803"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
Obtém o contexto de documento que descreve a posição do documento que está para se tornar ativa, o pacote de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppDocContext`  
 [out] Retorna um [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objeto que representa uma posição em um documento do arquivo de origem.  
  
## <a name="remarks"></a>Comentários  
 Nessa posição pode ser usada para mostrar o cursor, por exemplo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)