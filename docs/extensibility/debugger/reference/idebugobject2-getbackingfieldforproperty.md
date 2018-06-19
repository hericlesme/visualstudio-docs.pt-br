---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7729f55c93274796d3c81f280618653b873bc40b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122503"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtém o campo ou variável (se houver) que pode ser fazendo a propriedade representada pelo objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppObject`  
 [out] Um [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto que descreve o campo de backup.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto representa uma propriedade de classe do código gerenciado, ou seja, um método com um get e/ou o acessador set. Essas propriedades geralmente requerem uma variável para conter o valor manipulado pela propriedade. Essa variável é conhecida como o campo de backup. Se não houver nenhum campo de backup para o objeto, certifique-se de retornar um valor nulo: alguns chamadores não pode prestar atenção para o valor de retorno, mas ficará em vez disso, para ver se um valor nulo foi retornado em `ppObject`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)