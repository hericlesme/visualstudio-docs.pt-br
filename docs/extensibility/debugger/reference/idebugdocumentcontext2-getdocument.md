---
title: IDebugDocumentContext2::GetDocument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46ca66ca27988f0c147f87dd170b6af1ee59bafd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
Obtém o documento que contém este contexto de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDocument(   
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppDocument`  
 [out] Retorna um [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objeto que representa o documento que contém este contexto de documento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é para os mecanismos de depuração que fornecem documentos diretamente do IDE. Caso contrário, esse método deve retornar `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)