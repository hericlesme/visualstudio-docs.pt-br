---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b5210859115947115bce6525cd5b6cd15c4d59d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102389"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Cria um enumerador para as classes base desta classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de classes base. Retorna um valor nulo se não houver nenhuma classe base.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK, retorna S_SH_NO_BASE_CLASSES se não houver nenhuma classe base (e o `ppEnum` parâmetro for definido como um valor nulo); caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As classes base do objeto de enumerador são especificadas na ordem da classe base mais imediata (ou mais derivada) para a classe base mais remota. Por exemplo, considerando as classes C++:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 A enumeração retornaria as classes base na ordem `Level2`, `Level1`, `Root`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)