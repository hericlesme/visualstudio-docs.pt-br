---
title: Typedef JsContextRef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>Typedef JsContextRef
Uma referência a um contexto de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>Comentários  
 Cada contexto de script contém seu próprio objeto global, distinto do objeto global de outros contextos de script.  
  
 Muitas APIs de hospedagem Chakra exigem um contexto de script "ativo", que pode ser definido usando `JsSetCurrentContext`. As APIs de hospedagem Chakra que exigem uma definição de contexto atual observarão esse fato explicitamente em sua documentação.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)