---
title: TYPE_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d6888d2680cffbde132885d730cd35f6e509c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="typeinfo"></a>TYPE_INFO
Essa estrutura especifica vários tipos de informações sobre o tipo do campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 dwKind  
 Um valor da [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração que determina como interpretar a união.  
  
 type.typeMeta  
 [C++] Contém uma [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) estrutura se `dwKind` é `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [C++] Contém uma [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) estrutura se `dwKind` é `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [C++] Contém uma [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) estrutura se `dwKind` é `TYPE_KIND_BUILT`.  
  
 Type.Unused  
 Preenchimento não utilizado.  
  
 tipo  
 Nome da união.  
  
 unionmember  
 [Apenas c#] Marshaling para o tipo de estrutura apropriada com base em `dwKind`.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método em que ele é preenchido. Como o conteúdo da estrutura é interpretado se baseia o `dwKind` campo.  
  
> [!NOTE]
>  [C++] Se `dwKind` é igual a `TYPE_KIND_BUILT`, em seguida, é necessário liberar subjacente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) na destruição de objeto a `TYPE_INFO` estrutura. Isso é feito chamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [Apenas c#] A tabela a seguir mostra como interpretar o `unionmember` membro para cada tipo de tipo. O exemplo mostra como isso é feito para um tipo de tipo.  
  
|`dwKind`|`unionmember`interpretado como|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como interpretar o `unionmember` membro o `TYPE_INFO` estrutura em c#. Este exemplo mostra apenas um tipo de interpretação (`TYPE_KIND_METADATA`), mas os outros são interpretados exatamente da mesma maneira.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)