---
title: JsNativeFunction Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568076"
---
# <a name="jsnativefunction-typedef"></a>Typedef JsNativeFunction
Um função de retorno.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 receptor  
 Um objeto `Function` que representa a função sendo invocada.  
  
 isConstructCall  
 Indica se essa é uma chamada regular ou uma 'nova' chamada.  
  
 arguments  
 Os argumentos da chamada.  
  
 argumentCount  
 O número de argumentos.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 O resultado da chamada, se houver alguma.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)