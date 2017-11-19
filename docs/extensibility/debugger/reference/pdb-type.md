---
title: PDB_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PDB_TYPE
helpviewer_keywords: PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eadfeb8ffdf7cdb1b51951c466f0cb94283da6a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="pdbtype"></a>PDB_TYPE
Essa estrutura Especifica informações sobre um tipo de campo obtido um símbolo PDB.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ulAppDomainID  
 ID do aplicativo do qual o símbolo foi originada. Isso é usado para identificar exclusivamente uma instância do aplicativo.  
  
 guidModule  
 O GUID do módulo que contém esse campo.  
  
 symid  
 A ID do símbolo que corresponde a esse campo.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é exibido como parte da união no [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estrutura quando o `dwKind` campo do `TYPE_INFO` estrutura é definida como `TYPE_KIND_PDB` (um valor da [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)