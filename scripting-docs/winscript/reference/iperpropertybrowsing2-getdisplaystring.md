---
title: IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be6f665d1f63966b3828868f4fb8fbf1cae002e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Obtém uma cadeia de caracteres para exibir tipos que não são visíveis inerentemente texto retornado é um nome que descreve a propriedade e pode ser exibida na interface do usuário do chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dispid`  
 [in] Expedir o identificador da propriedade cujo nome de exibição é solicitado.  
  
 `pBstr`  
 [out] Ponteiro para o `BSTR` que contém o nome de exibição para a propriedade identificada por `dispID`.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres retornada não é um valor válido da propriedade. É apenas uma exibição de cadeia de caracteres da propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)