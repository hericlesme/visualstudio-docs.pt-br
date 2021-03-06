---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd73955835f8aff0047995a690da03e5ab0305d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105821"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtém a classe que inclui essa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClassField`  
 [out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) a classe de objeto que representa o delimitador. Retorna um valor nulo se não houver nenhuma classe de delimitador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se a classe é representado por esse [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto é uma classe aninhada, em seguida, o `ppClassField` parâmetro retorna um `IDebugClassField` a classe de objeto que representa o delimitador. Por exemplo, dada a definição de classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Chamando o `GetEnclosingClass` método no `IDebugClassField` objeto representando o `NestedClass` classe retorna uma `IDebugClassField` que representa a classe de objeto `RootClass`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)