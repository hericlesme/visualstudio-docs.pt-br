---
title: DEBUG_ADDRESS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05c6e00591271fc0a8c074e8018bd780c75d1857
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462073"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [DEBUG_ADDRESS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-address).  
  
Essa estrutura representa um endereço.  
  
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
 O token de identificação de classe ou tipo desse endereço.  
  
> [!NOTE]
>  Esse valor é específico para um provedor de símbolo e, portanto, não tem nenhum significado geral diferente de como um identificador para um tipo de classe.  
  
 Addr  
 Um [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura, que contém uma união de estruturas que descrevem os tipos de endereço individual. O valor `addr`.`dwKind` é proveniente de [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração, que explica como interpretar a união.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método a ser preenchido.  
  
 **Aviso [C++]**  
  
 Se `addr.dwKind` está `ADDRESS_KIND_METADATA_LOCAL` e, se `addr.addr.addrLocal.pLocal` não é um valor nulo, em seguida, você deve chamar `Release` no ponteiro de token:  
  
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

