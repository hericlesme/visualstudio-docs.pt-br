---
title: 'Erro: Tempo limite durante a depuração de serviços da Web | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467528"
---
# <a name="error-timeout-while-debugging-web-services"></a>Erro: tempo limite durante a depuração de serviços Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: tempo limite enquanto depuração de serviços da Web](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services).  
  
Quando você estiver acessando um serviço Web XML do código de chamada, a chamada pode exceder o tempo limite e você não poderá continuar a depuração. Você pode ver uma mensagem de erro como essa.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Solução  
 Para evitar esse problema, defina o tempo limite para a chamada ao serviço Web XML como infinito, conforme exibido neste exemplo:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



