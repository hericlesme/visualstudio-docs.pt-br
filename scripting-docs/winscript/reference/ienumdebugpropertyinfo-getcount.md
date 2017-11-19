---
title: IEnumDebugPropertyInfo::GetCount | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugPropertyInfo::GetCount
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16597adcc64ec6096e5a347d10c47671cbc2ea37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugpropertyinfogetcount"></a>IEnumDebugPropertyInfo::GetCount
Obtém o número de `DebugPropertyInfo` estruturas no enumerador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcelt`  
 [out] Retorna o número de `DebugPropertyInfo` estruturas no enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)