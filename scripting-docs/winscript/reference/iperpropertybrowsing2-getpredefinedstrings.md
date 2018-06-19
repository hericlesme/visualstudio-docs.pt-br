---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729246"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permite que o chamador preencher uma caixa de listagem com uma matriz de contado de ponteiros de cadeia de caracteres que representam os valores possíveis para essa propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dispid`  
 [in] Identificador de expedição da propriedade para o qual o chamador está solicitando a lista de cadeia de caracteres.  
  
 `pCaStrings`  
 [out] Ponteiro para uma estrutura de matriz alocada pelo chamador, contado que contém a contagem do elemento e o endereço de uma matriz alocada pelo método de ponteiros de cadeia de caracteres. Se o método falhar, nenhuma memória é alocada e o conteúdo da estrutura é indefinido.  
  
 `pCaCookies`  
 [out] Ponteiro para a estrutura de matriz alocada pelo chamador, contado que contém a contagem do elemento e o endereço de uma matriz de DWORDs alocada pelo método. Se o método falhar, nenhuma memória é alocada e o conteúdo da estrutura é indefinido.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)