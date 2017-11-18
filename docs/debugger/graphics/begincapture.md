---
title: BeginCapture | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8774b60f8791373b312437a3e554d17f9582f07f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="begincapture"></a>BeginCapture
Inicia um intervalo de captura terminará com `EndCapture`.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um intervalo de captura abrange um subconjunto de um quadro, como quando você deseja capturar informações apenas sobre um determinado tipo de chamada de desenho de gráficos. Se o intervalo de captura abrange uma chamada para apresentar, dois quadros de informações de gráficos são capturados. O primeiro quadro abrange o intervalo entre a chamada para `BeginCapture` e a chamada para apresentar; o segundo quadro abrange o intervalo entre o primeiro evento Direct3D após a chamada para apresentar e a chamada para `EndCapture`.  
  
 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e registrar informações de gráficos — ou seja, você deverá ter chamado [Init](init.md) por meio de uma instância do `VsgDbg` classe antes de chamar `BeginCapture` ou `EndCapture`.  
  
## <a name="see-also"></a>Consulte também  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)