---
title: METADATA_ADDRESS_METHOD | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_METHOD
helpviewer_keywords: METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d94087b9408afcc82dda8715faa643fa4f348cf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="metadataaddressmethod"></a>METADATA_ADDRESS_METHOD
Esta estrutura representa o endereço de um método de uma classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```csharp  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## <a name="terms"></a>Termos  
 tokMethod  
 A ID do método.  
  
 [C++] `_mdToken` é um `typedef` para 32 bits `int`.  
  
 dwOffset  
 O deslocamento desde o início de classe para este método (pode representar o deslocamento para a vtable).  
  
 versão do DW  
 A versão do método (esse valor é exclusivo para o provedor de símbolo).  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é parte da união no [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura quando o `dwKind` campo do `DEBUG_ADDRESS_UNION` estrutura é definida como `ADDRESS_KIND_METHOD` (um valor da [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)