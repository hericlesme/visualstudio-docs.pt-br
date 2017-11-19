---
title: IDebugObject::SetValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::SetValue
helpviewer_keywords: IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e4a4311d5e115e20d23096a6ca1e3bce2dcbea6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Define o valor do objeto de consecutivos de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pValue`  
 [in] Uma matriz de bytes que representa o novo valor.  
  
 `nSize`  
 [in] O tamanho do valor em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os valores na matriz são copiados para este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto, substituindo qualquer valor existente. O tamanho do novo valor pode ser maior ou menor que o valor existente. Isso `IDebugObject` não pode ser uma referência nula.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)