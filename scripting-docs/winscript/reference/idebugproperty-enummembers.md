---
title: IDebugProperty::EnumMembers | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera os membros de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 [in] Especifica o `DBGPROP_INFO_FLAGS` constantes que determinam quais campos nas estruturas de propriedade de depuração enumerados são devem ser preenchidos.  
  
 `nRadix`  
 [in] Base a ser usada na interpretação todas as informações numéricas.  
  
 `refiid`  
 [in] Este IID é passado para o enumerador de filtragem. O IID é uma da `IDebugPropertyEnumType` as interfaces que herdam `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Retorna o `IEnumDebugPropertyInfo` interface que enumera as propriedades do membro.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Interface IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)