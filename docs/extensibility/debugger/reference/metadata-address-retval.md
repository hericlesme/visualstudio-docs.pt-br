---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_RETVAL
helpviewer_keywords: METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51db1e429e363a653ddde4948f7519e547f99a19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Esta estrutura representa um valor de retorno de uma função ou método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>Termos  
 tokMethod  
 A ID do método esse valor de retorno é.  
  
 dwCorType  
 O tipo base do valor de retorno. Este é um valor da `CorElementType` enumeração definida no [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] arquivo corhdr do SDK.  
  
 dwSigSize  
 O tamanho da assinatura do valor de retorno (conforme armazenado no `rgSig`).  
  
 rgSig  
 Uma matriz de bytes que cria a assinatura do valor de retorno.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é parte da união no [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura quando o `dwKind` campo do `DEBUG_ADDRESS_UNION` estrutura é definida como `ADDRESS_KIND_RETVAL` (um valor da [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)