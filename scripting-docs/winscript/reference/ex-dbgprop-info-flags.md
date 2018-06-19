---
title: EX_DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0af0de81c0253b72fe432cb3cefe11c362bc2ec4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640896"
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
Usado para especificar `ExtendedDebugPropertyInfo` campos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>Membros  
 EX_DBGPROP_INFO_ID  
 Inicializa o identificador para a propriedade.  
  
 EX_DBGPROP_INFO_NTYPE  
 Inicializa o tipo da propriedade.  
  
 EX_DBGPROP_INFO_NVALUE  
 Inicializa o valor da propriedade.  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 Inicializa o `plb` campo.  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 Inicializa o `pDebugExtProp` campo que contém um `IDebugExtendedProperty` interface.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [Interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)