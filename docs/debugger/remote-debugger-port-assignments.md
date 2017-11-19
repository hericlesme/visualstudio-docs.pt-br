---
title: "As atribuições de porta do depurador remoto | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb5f72669068855dfcff954faae5dbe6009a52f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugger-port-assignments"></a>Atribuições de porta do depurador remoto
O depurador remoto do Visual Studio pode ser executado como um aplicativo ou como um serviço em segundo plano. Quando ele é executado como um aplicativo, ele usa uma porta que é atribuída por padrão da seguinte maneira:  

-   O Visual Studio 2017:4022

-   O Visual Studio 2015:4020  
  
-   O Visual Studio 2013:4018  
  
-   O Visual Studio 2012:4016  
  
 Em outras palavras, o número da porta atribuída ao depurador remoto é incrementado em 2 para cada versão. Você pode definir um número de porta diferente da que você deseja. Explicaremos como configurar números de porta em uma seção posterior.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>A porta do depurador remoto em sistemas operacionais de 32 bits  
 4022 TCP (no Visual Studio de 2017) é a porta principal e é necessário para todos os cenários. Você pode configurar isso na linha de comando ou a janela de depurador remoto.  
  
 Na janela de depurador remoto, clique em **Ferramentas > Opções**e defina o número da porta TCP/IP.  
  
 Na linha de comando, iniciar o depurador remoto com o **porta/** alternar: **msvsmon /port \<número da porta >**.  
  
 Você pode encontrar o depurador remoto opções de linha de comando na Ajuda de depuração remota (pressione **F1** ou clique em **Ajuda > uso** na janela de depurador remoto).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>A porta do depurador remoto em sistemas operacionais de 64 bits  
 Quando a versão de 64 bits do depurador remoto é iniciada, ele usa a porta 4022 por padrão.  Se você depurar um processo de 32 bits, a versão de 64 bits do depurador remoto inicia uma versão de 32 bits do depurador remoto na porta 4023. Se você executar o depurador remoto de 32 bits, ele usa 4022 e 4023 não é usado.  
  
 Essa porta é configurável na linha de comando: **Msvsmon /wow64port \<número da porta >**.  
  
## <a name="the-discovery-port"></a>A porta de descoberta  
 UDP 3702 é usado para localizar instâncias em execução do depurador remoto na rede (por exemplo, o **localizar** caixa de diálogo no **anexar ao processo** caixa de diálogo). Ele é usado somente para descobrir um computador executando o depurador remoto, portanto, é opcional se você tiver alguma outra maneira de saber o nome do computador ou endereço IP do computador de destino. Isso é uma porta padrão para a descoberta, para que o número da porta não pode ser configurado.  
  
 Se você não quiser habilitar a descoberta, você pode iniciar msvsmon da linha de comando com a descoberta desabilitada: **/nodiscovery Msvsmon**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Portas do depurador remoto no Azure  
 As seguintes portas são usadas pelo depurador remoto no Azure. As portas no serviço de nuvem são mapeadas para as portas na VM individual. Todas as portas são TCP.  
  
||||  
|-|-|-|  
|**Conexão**|**Porta no serviço de nuvem**|**Porta na máquina virtual**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)