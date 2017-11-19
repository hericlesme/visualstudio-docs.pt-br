---
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumConstructors
helpviewer_keywords: IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24ae27acb2dd78b086a8b94e28c3de705cd710ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Cria um enumerador para os construtores para esta classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cMatch`  
 [in] Um valor da [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) enumeração que especifica o tipo de construtores para enumeração.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de construtores. Retorna um valor nulo se não houver nenhum construtor.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum construtor. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é uma [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) que descreve um método de construtor do objeto.  
  
 A lista de construtores normalmente não inclui os construtores padrão fornecidos por um compilador.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)