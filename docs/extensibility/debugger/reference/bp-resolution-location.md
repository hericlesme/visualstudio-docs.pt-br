---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 032228596773d4a5a164f904c1caae161b693f64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
Especifica a estrutura do local de resolução do ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Membros  
 `bpType`  
 Um valor da [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumeração que especifica como interpretar o `bpResLocation` união ou `unionmemberX` membros.  
  
 `bpResLocation.bpresCode`  
 [C++] Contém o [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) estrutura se `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 [C++] Contém o [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) estrutura se `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 [C++] Um espaço reservado.  
  
 `unionmember1`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
 `unionmember2`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
 `unionmember3`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
 `unionmember4`  
 [Apenas c#] Consulte os comentários sobre como interpretar.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é membro do [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) e [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estruturas.  
  
 [Apenas c#] O `unionmemberX` membros são interpretados de acordo com a tabela a seguir. Examine a coluna à esquerda para a `bpType` valor em, em seguida, para determinar o que cada `unionmemberX` membro representa e empacotar o `unionmemberX` adequadamente. Consulte o exemplo de uma maneira de interpretar esta estrutura em c#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (expressão de dados)|`string` (nome da função)|`string` (nome da imagem)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como interpretar o `BP_RESOLUTION_LOCATION` estrutura em c#.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)