---
title: 'Como: depurar um serviço WCF auto-hospedado | Microsoft Docs'
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
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1e87af205a88e84942eb4958876c2030a175065
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475821"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Como depurar um serviço WCF auto-hospedado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: depurar um serviço do WCF auto-hospedado](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-a-self-hosted-wcf-service).  
  
Um *serviço auto-hospedado* é um serviço WCF que não é executado dentro do IIS, o Host de serviço do WCF, ou o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server. A maneira mais fácil de depurar um WCF auto-hospedado é configurar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para iniciar o cliente e servidor quando você escolhe **iniciar depuração** sobre o **depurar** menu.  
  
 Se o serviço WCF está sendo auto-hospedado internamente ou é um processo que não pode ser iniciado dessa maneira, como serviço do NT, você não pode usar este método. Em vez disso, execute um destes procedimentos:  
  
-   Anexe manualmente o depurador ao processo de hospedagem. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     – ou —  
  
-   Inicie a depuração do cliente e inspecione uma chamada para o serviço. Isso requer que você habilite a depuração no arquivo app.config. Para obter mais informações, [limitações na depuração de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Para iniciar o cliente e o host do Visual Studio  
  
1.  Crie uma solução do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contém os projetos de cliente e de servidor.  
  
2.  Configurar a solução para iniciar processos do cliente e servidor quando você escolhe **inicie** sobre o **depurar** menu.  
  
    1.  Na **Gerenciador de soluções**, clique com botão direito no nome da solução.  
  
    2.  Clique em **definir projetos de inicialização**.  
  
    3.  No **Solution \<nome > propriedades** caixa de diálogo, selecione **vários projetos de inicialização**.  
  
    4.  No **vários projetos de inicialização** grade, na linha que corresponde ao projeto do servidor, clique em **ação** e escolha **iniciar**.  
  
    5.  Na linha que corresponde ao projeto do cliente, clique em **ação** e escolha **iniciar**.  
  
    6.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando serviços WCF](../debugger/debugging-wcf-services.md)   
 [Limitações na depuração de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Como intervir em serviços WCF](../debugger/how-to-step-into-wcf-services.md)



