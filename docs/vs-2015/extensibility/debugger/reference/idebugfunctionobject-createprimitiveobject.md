---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
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
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320930a86a58b51155b3f7400ea791135c321d95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474171"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugFunctionObject::CreatePrimitiveObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject).  
  
Cria um objeto de dados primitivos, como um inteiro simples.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ot`  
 [in] Um valor a partir de [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumeração que representa o tipo primitivo para criar.  
  
 `ppObject`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto recém-criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método para criar um objeto que representa um objeto primitivo que é um parâmetro para a função que é representado pela [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface. Por exemplo, se a cadeia de caracteres de expressão for "myString(5)", esse método seria usado para criar um objeto que representa o inteiro 5.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

