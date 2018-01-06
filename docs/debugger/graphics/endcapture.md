---
title: EndCapture | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6f717d8b1e95531f0b758a88db48b610b343ee60
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endcapture"></a>EndCapture
Termina um intervalo de captura foi iniciado com `BeginCapture`.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um intervalo de captura abrange um subconjunto de um quadro, como quando você deseja capturar informações apenas sobre um determinado tipo de chamada de desenho de gráficos. Se o intervalo de captura abrange uma chamada para apresentar, dois quadros de informações de gráficos são capturados. O primeiro quadro abrange o intervalo entre a chamada para `BeginCapture` e a chamada para apresentar; o segundo quadro abrange o intervalo entre o primeiro evento Direct3D após a chamada para apresentar e a chamada para `EndCapture`.  
  
 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e registrar informações de gráficos — ou seja, você deverá ter chamado [Init](init.md) por meio de uma instância do `VsgDbg` classe antes de chamar `BeginCapture` ou `EndCapture`.  
  
## <a name="see-also"></a>Consulte também  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)