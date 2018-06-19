---
title: CONTEXT_COMPARE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0563f037f77c18cc5e686c1ea6acf429c91ad06d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108577"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Especifica os critérios para comparar dois contextos de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Membros  
 CONTEXT_EQUAL  
 Localize o contexto de memória primeiro na lista que é igual para o contexto de memória de destino.  
  
 CONTEXT_LESS_THAN  
 Localize o contexto de memória primeiro na lista que é menor que o contexto de memória de destino.  
  
 CONTEXT_GREATER_THAN  
 Localize o contexto de memória primeiro na lista que é maior do que o contexto de memória de destino.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Localize o contexto de memória primeiro na lista que é menor ou igual ao contexto de memória de destino.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Localize o contexto de memória primeiro na lista que é maior que ou igual ao contexto de memória de destino.  
  
 CONTEXT_SAME_SCOPE  
 Localize o contexto de memória primeiro na lista que está no mesmo escopo que o contexto de memória de destino.  
  
 CONTEXT_SAME_FUNCTION  
 Localize o contexto de memória primeiro na lista que está na mesma função que o escopo de memória de destino.  
  
 CONTEXT_SAME_MODULE  
 Localize o contexto de memória primeiro na lista que está no mesmo módulo como o contexto de memória de destino.  
  
 CONTEXT_SAME_PROCESS  
 Localize o contexto de memória primeiro na lista que está no mesmo processo que o contexto de memória de destino.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) método.  
  
 Esses valores são usados para localizar o contexto de memória primeiro em uma lista que satisfaz os critérios de comparação especificado. Um contexto de memória é fornecido uma lista de contextos de memória para comparar a próprio contra por meio de `IDebugMemoryContext2::Compare` método. O contexto de memória primeiro na lista para o qual o operador de comparação é `true` , em seguida, é retornado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)