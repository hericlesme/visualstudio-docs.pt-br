---
title: CaptureCurrentFrame | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 739f2a9a97fefcb1bc57c7987d5afec7a09ff4ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Captura o restante do quadro atual para o arquivo de log do gráfico.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Comentários  
 Se outro captura está em andamento — como uma captura iniciada com o `BeginCapture` função — que captura é concluída e registrada no log de gráficos como um quadro distinto. Logo depois, diagnóstico de gráficos começa a capturar o restante do quadro atual, que também é registrado como um quadro distinto. Final do quadro atual é marcada por uma chamada para apresentar.  
  
 Para capturar um quadro, você deve preparar seu aplicativo para capturar e registrar informações de gráficos — ou seja, você deverá ter chamado [Init](init.md) por meio de uma instância do `VsgDbg` classe antes de chamar `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Consulte também  
 [Init](init.md)   
 [BeginCapture](begincapture.md)