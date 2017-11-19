---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords: IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b533423da8152dd23df6d32da3361c99ad032b7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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