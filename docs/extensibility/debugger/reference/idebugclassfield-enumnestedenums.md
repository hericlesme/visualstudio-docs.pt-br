---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ea28f2a455d3528f083ba2acb2e9e4ad8989319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103023"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Cria um enumerador para os enumeradores aninhados dessa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de enumerações aninhadas. Retorna um valor nulo se não houver nenhum enumerações aninhadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver nenhum enumeradores aninhadas. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é uma [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que descreve uma enumeração aninhada.  
  
 Uma enumeração declarada dentro de uma classe é considerada uma enumeração aninhada. Por exemplo, com base em:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 O `EnumNestedEnums` método retornaria um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que contém um [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa o `NestedEnum` enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)