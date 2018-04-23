---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 519281487e85ec7dffc0e7bb470d044dc2bae885
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Esse método recupera a exceção associada a um objeto, se houver.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppException`  
 [out] Retorna o objeto que representa a exceção.  
  
 `ppField`  
 [out] Retorna o objeto que representa um campo que pode ter causado a exceção (Isso pode ser um valor nulo).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
> [!NOTE]
>  Para verificar se há uma exceção, verifique o valor retornado por `ppException`: se ele é um valor nulo, nenhuma exceção é associada este objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)