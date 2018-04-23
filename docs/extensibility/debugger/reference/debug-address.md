---
title: DEBUG_ADDRESS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07312208967aeccfbd81f44587f84a43dfebf4c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Esta estrutura representa um endereço.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Termos  
 ulAppDomainID  
 A ID de processo.  
  
 guidModule  
 O GUID do módulo que contém esse endereço.  
  
 tokClass  
 O token que identifica a classe ou o tipo desse endereço.  
  
> [!NOTE]
>  Esse valor é específico para um provedor de símbolo e, portanto, não tem nenhum significado geral de como um identificador para um tipo de classe.  
  
 Endereço  
 Um [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura, que contém uma união de estruturas que descrevem os tipos de endereço individual. O valor `addr`.`dwKind` é proveniente do [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração, que explica como interpretar a união.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método a ser preenchido.  
  
 **Aviso [C++]**  
  
 Se `addr.dwKind` é `ADDRESS_KIND_METADATA_LOCAL` e se `addr.addr.addrLocal.pLocal` não é um valor nulo, em seguida, você deve chamar `Release` no ponteiro token:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)