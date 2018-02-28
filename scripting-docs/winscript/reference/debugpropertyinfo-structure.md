---
title: Estrutura DebugPropertyInfo | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debugpropertyinfo-structure"></a>Estrutura DebugPropertyInfo
Descreve um objeto de natureza hierárquica que tem o nome, tipo e valor. Ele é usado para descrever as propriedades de depuração de variáveis locais, parâmetros, inspecionar variáveis e expressões e registra.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Membros  
 dwValidFields  
 Um tipo de dados enumerado usado para especificar quais campos são inicializados.  
  
 bstrName  
 O nome da propriedade em um contexto.  
  
 bstrType  
 O tipo de propriedade, como cadeia de caracteres formatada.  
  
 bstrValue  
 O valor da propriedade, como cadeia de caracteres formatada.  
  
 bstrFullName  
 O nome completo da propriedade.  
  
 dwAttrib  
 Uma enumeração que especifica os sinalizadores para os atributos de propriedade de depuração.  
  
 pDebugProp  
 O `IDebugProperty` descrito pelas informações neste `DebugPropertyInfo` estrutura.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)