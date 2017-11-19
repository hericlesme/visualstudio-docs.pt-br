---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_ADDRESS_UNION
helpviewer_keywords: DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7f2f01ee30949fc5b82f2bba868e433a4f3a14e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
Descreve os diferentes tipos de endereços.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>Termos  
 dwKind  
 Um valor da [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração, especificando como interpretar a união.  
  
 addr.addrNative  
 [C++] Contém o [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) estrutura se `dwKind` = ADDRESS_KIND_NATIVE.  
  
 addr.addrThisRel  
 [C++] Contém o[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) estrutura se `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.  
  
 addr.addUPhysical  
 [C++] Contém o[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) estrutura se `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.  
  
 addr.addrMethod  
 [C++] Contém o[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) estrutura se `dwKind` = ADDRESS_KIND_METHOD.  
  
 addr.addrField  
 [C++] Contém o[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) estrutura se `dwKind` = ADDRESS_KIND_FIELD.  
  
 addr.addrLocal  
 [C++] Contém o[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) estrutura se `dwKind` = ADDRESS_KIND_LOCAL.  
  
 addr.addrParam  
 [C++] Contém o[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) estrutura se `dwKind` = ADDRESS_KIND_PARAM.  
  
 addr.addrArrayElem  
 [C++] Contém o[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) estrutura se `dwKind` = ADDRESS_KIND_ARRAYELEM.  
  
 addr.addrRetVal  
 [C++] Contém o[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) estrutura se `dwKind` = ADDRESS_KIND_RETVAL.  
  
 addr.Unused  
 Preenchimento [C++].  
  
 Endereço  
 [C++] O nome da união.  
  
 unionmember  
 [Apenas c#] Esse valor precisa ser empacotado para o tipo de estrutura apropriada com base em `dwKind`. Consulte os comentários para a associação entre `dwKind` e interpretação da união.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é parte do [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura e representa um de um número de tipos diferentes de endereços (o `DEBUG_ADDRESS` estrutura é preenchida por uma chamada para o [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método).  
  
 [Apenas c#] A tabela a seguir mostra como interpretar o `unionmember` membro para cada tipo de endereço. O exemplo mostra como isso é feito para um tipo de endereço.  
  
|`dwKind`|`unionmember`interpretado como|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como interpretar um tipo de endereço (`METADATA_ADDRESS_ARRAYELEM`) da `DEBUG_ADDRESS_UNION` estrutura em c#. Os elementos restantes podem ser interpretados exatamente da mesma maneira.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)