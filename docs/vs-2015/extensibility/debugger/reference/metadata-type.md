---
title: METADATA_TYPE | Microsoft Docs
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
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8d7b6f6e38a92be62c676e69197d990cb53989db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467582"
---
# <a name="metadatatype"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [METADATA_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/metadata-type).  
  
Essa estrutura Especifica informações sobre um tipo de campo tirado de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ulAppDomainID  
 ID do aplicativo do qual o símbolo foi originada. Isso é usado para identificar exclusivamente uma instância do aplicativo.  
  
 guidModule  
 O GUID do módulo que contém esse campo.  
  
 tokClass  
 A ID do token metadados desse tipo.  
  
 [C++] `_mdToken` é um `typedef` de 32 bits `int`.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é exibido como parte da união na [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estrutura quando o `dwKind` campo dos `TYPE_INFO` estrutura é definida como `TYPE_KIND_METADATA` (um valor da [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração).  
  
 O `tokClass` valor é um token de metadados que identifica exclusivamente um tipo. Para obter detalhes sobre como interpretar os bits superiores do que a ID do token de metadados, consulte a `CorTokenType` enumeração no arquivo corhdr. h no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)

