---
title: 'Como: intervir em serviços WCF | Microsoft Docs'
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
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b779c8bc2e6da3975f1f70265482c706c9141375
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466382"
---
# <a name="how-to-step-into-wcf-services"></a>Como intervir em serviços WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: intervir em serviços WCF](https://docs.microsoft.com/visualstudio/debugger/how-to-step-into-wcf-services).  
  
No [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], você pode entrar em um serviço WCF. Se o serviço WCF estiver na mesma solução do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que o cliente, você poderá usar pontos de interrupção no serviço WCF.  
  
 Para que a depuração funcione, você deve ter a depuração habilitada no arquivo app.config ou Web.config. Para obter informações sobre como habilitar a depuração e limitações para entrar em serviços WCF, consulte [limitações na depuração de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Para entrar em um serviço WCF  
  
1.  Crie uma solução do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contém os projetos de cliente WCF e serviço WCF.  
  
2.  No Solution Explorer, o projeto de cliente do WCF com o botão direito e, em seguida, clique em **definir como projeto de inicialização**.  
  
3.  Habilite a depuração no arquivo app.config ou web.config. Para obter mais informações, consulte [limitações na depuração de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Defina um ponto de interrupção no local no projeto de cliente onde você deseja iniciar a entrada. Normalmente, isso será imediatamente antes da chamada de WCF.  
  
5.  Execute o ponto de interrupção e inicie a entrada. O depurador entrará no serviço automaticamente.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando serviços WCF](../debugger/debugging-wcf-services.md)   
 [Limitações na depuração de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Como depurar um serviço WCF auto-hospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



