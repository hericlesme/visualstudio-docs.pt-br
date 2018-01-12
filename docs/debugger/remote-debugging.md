---
title: "Depuração remota no Visual Studio | Microsoft Docs"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: hero-article
f1_keywords: vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a0eb590549578ac9aea824f52c8192c97dce94f2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="remote-debugging"></a>Depuração remota
Você pode depurar um aplicativo do Visual Studio que foi implantado em um computador diferente. Para fazer isso, você deve usar o depurador remoto do Visual Studio.

Para obter instruções detalhadas sobre a depuração remota, consulte estes tópicos.

|Cenário|Link|
|-|-|-|
|ASP.NET|[Depuração ASP.NET Core remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) ou [ASP.NET de depuração remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# ou Visual Basic|[Um c# ou Visual Basic Project a depuração remota](../debugger/remote-debugging-csharp.md)|
|C++|[Depuração remota de um projeto em C++](../debugger/remote-debugging-cpp.md)|
|Aplicativos universais do Windows (UWP)|[Executar aplicativos UWP em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) e [depurar um pacote de aplicativo instalado](../debugger/debug-installed-app-package.md)|
|Azure|[ASP.NET de depuração remota no Azure](remote-debugging-azure.md)|
|Malha do serviço do Azure|[Depurar um aplicativo de malha do serviço remoto](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).|

Se você apenas deseja baixar e instalar o depurador remoto e não é necessário quaisquer instruções adicionais para seu cenário, siga as etapas neste artigo.
  
## <a name="download-and-install-the-remote-tools"></a>Baixe e instale as ferramentas remotas  

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="fileshare_msvsmon"></a>(Opcional) Para executar o depurador remoto de um compartilhamento de arquivo

Você pode encontrar o depurador remoto (**msvsmon.exe**) em um computador com Visual Studio Community, Professional ou Enterprise já instalado. Para alguns cenários, a maneira mais fácil de configurar a depuração remota é executar o depurador remoto (msvsmon.exe) de um compartilhamento de arquivos. Para limitações de uso, consulte a página de Ajuda do depurador remoto (**Ajuda > uso** no depurador remoto).

1. Localizar **msvsmon.exe** no diretório correspondente de sua versão do Visual Studio. Para o Visual Studio Enterprise 2017:

      **Programa arquivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Programa arquivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Compartilhamento de **depurador remoto** pasta no computador do Visual Studio.

3. No computador remoto, execute **msvsmon.exe**. Siga o [instruções de instalação](#bkmk_setup).

> [!TIP] 
> Para instalação de linha de comando e referência de linha de comando, consulte a página de ajuda para **msvsmon.exe** digitando ``msvsmon.exe /?`` na linha de comando no computador com Visual Studio instalado (ou vá para **Ajuda > uso**do depurador remoto).
  
## <a name="requirements_msvsmon"></a> Requisitos

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]
  
## <a name="set-up-the-remote-debugger"></a>Configurar o depurador remoto  

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a>Configurar o depurador remoto  
Depois de ele ter iniciado pela primeira vez, você pode alterar alguns aspectos da configuração do depurador remoto.
  
-   Se você precisa adicionar permissões para outros usuários para se conectar ao depurador remoto, escolha **Ferramentas > permissões**. Você deve ter privilégios de administrador para conceder ou negar permissões.

     > [!IMPORTANT] 
     > Você pode executar o depurador remoto em uma conta de usuário diferente da conta de usuário que você está usando no computador do Visual Studio, mas você deve adicionar a conta de usuário diferente para permissões do depurador remoto. 

     Como alternativa, você pode iniciar o depurador remoto na linha de comando com o **/ permitir \<nome de usuário >** parâmetro: **msvsmon / permitir \< username@computer>**.
  
-   Se você precisar alterar o modo de autenticação ou o número da porta ou especificar um valor de tempo limite para as ferramentas remotas: escolha **Ferramentas > Opções**.  
  
     Para obter uma lista dos números de porta usados por padrão, consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md).  
  
     > [!WARNING]
     >  Você também pode optar por executar as ferramentas remotas no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo não há nenhuma segurança de rede. Escolha o modo sem autenticação somente se você tiver certeza de que a rede não está em risco de tráfego mal-intencionado ou hostil.

##  <a name="bkmk_configureService"></a>(Opcional) Configurar o depurador remoto como um serviço
Para a depuração do ASP.NET e outros ambientes de servidor, você deve executar o depurador remoto como um administrador ou, se você deseja que ele sempre em execução, executar o depurador remoto como um serviço.
  
 Se você quiser configurar o depurador remoto como um serviço, siga estas etapas.  
  
1.  Localizar o **Assistente de configuração do depurador remoto** (rdbgwiz.exe). (Este é um aplicativo separado do depurador remoto.) Ele está disponível apenas quando você instala as ferramentas remotas. Ele não é instalado com o Visual Studio.  
  
2.  Começar a executar o Assistente de configuração. Quando a primeira página é exibida, clique em **próximo**.  
  
3.  Verifique o **executar o depurador remoto do Visual Studio 2015 como um serviço** caixa de seleção.  
  
4.  Adicione o nome da conta do usuário e senha.  
  
     Talvez seja necessário adicionar o **fazer logon como um serviço** direito de usuário desta conta (localizar **política de segurança Local** (secpol. msc) no **iniciar** página ou janela (ou tipo  **secpol** em um prompt de comando). Quando a janela é exibida, clique duas vezes em **atribuição de direitos de usuário**, em seguida, localizar **fazer logon como um serviço** no painel direito. Clique duas vezes nesse item. Adicione a conta de usuário para o **propriedades** janela e clique em **Okey**). Clique em **Avançar**.  
  
5.  Selecione o tipo de rede que você deseja que as ferramentas remotas para se comunicar com. Pelo menos um tipo de rede deve ser selecionado. Se os computadores são conectados por meio de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo doméstico ou de grupo de trabalho, você deve escolher os itens de segundo ou de terceiros. Clique em **Avançar**.  
  
6.  Se o serviço pode ser iniciado, você verá **você concluiu com êxito o Assistente de configuração de depurador Visual remoto Studio**. Se o serviço não pode ser iniciado, você verá **Falha ao concluir o Assistente de configuração de depurador Visual remoto Studio**. A página também oferece algumas dicas a seguir para iniciar o serviço.  
  
7.  Clique em **Finalizar**.  
  
 Neste ponto, o depurador remoto está em execução como um serviço. Você pode verificar isso acessando **painel de controle > serviços** e procurando **depurador remoto do Visual Studio 2015**.  
  
 Você pode parar e iniciar o serviço do depurador remoto do **painel de controle > serviços**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]
  
## <a name="see-also"></a>Consulte também  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)   
 [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Núcleo do ASP.NET em um computador remoto do IIS a depuração remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
