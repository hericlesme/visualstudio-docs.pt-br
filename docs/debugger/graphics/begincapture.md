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
ms.workload: multiple
ms.openlocfilehash: e1c7c0f57b919271c4880c9c1f2fbd8ca1dc964f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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