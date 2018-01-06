---
title: Executar aplicativos UWP em um computador remoto | Microsoft Docs
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: "43"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: ebae0886db71b0b06f346d6bd174951b1c5d4752
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-apps-on-a-remote-machine"></a>Executar aplicativos UWP em um computador remoto
![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
Para executar um aplicativo UWP em um computador remoto, você deve anexar a ela usando as ferramentas remotas do Visual Studio. As ferramentas remotas permitem executar, depurar, analisar e testar um aplicativo UWP que está em execução em um dispositivo de um segundo computador que está executando o Visual Studio. Em execução em um dispositivo remoto pode ser especialmente eficaz quando o computador do Visual Studio não oferece suporte à funcionalidade específica para aplicativos UWP, como toque, localização geográfica e orientação física. Este tópico descreve os procedimentos para configurar e iniciar uma sessão remota.

Em alguns cenários, as ferramentas remotas são instaladas automaticamente quando você implanta em um dispositivo remoto.

- Para PCs com Windows 10 que executam os criadores de atualização e versões posteriores, consulte [depurar um pacote de aplicativos instalado](debug-installed-app-package.md#remote). Ferramentas remotas serão instaladas automaticamente.
- Para dispositivos Windows 10 Xbox, IOT e HoloLens, consulte [depurar um pacote de aplicativos instalado](debug-installed-app-package.md#remote). Ferramentas remotas serão instaladas automaticamente.
- Para Windows Phone, você deve estar conectado fisicamente ao telefone, você deve instalar um [licença de desenvolvedor](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) (Windows Phone 8 e 8.1) ou habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development) (Windows Mobile 10), e você deve Selecione **dispositivo** como o destino de depuração. Ferramentas remotas não são necessários ou suporte.

Para PCs com Windows 8.1 e Windows 10 computadores executando a versão de atualização de um pre-do criador do Windows, você deve instalar as ferramentas remotas no computador remoto manualmente para poder depurar. Siga as instruções neste tópico.
  
##  <a name="BKMK_Prerequisites"></a> Pré-requisitos  
 Para depurar em um dispositivo remoto:  
  
-   O dispositivo remoto e o computador com o Visual Studio devem estar conectados por uma rede ou diretamente por um cabo Ethernet. Não há suporte à depuração pela Internet.  

- O dispositivo remoto deve ser habilitado para o desenvolvimento.

    - Para dispositivos Windows 8 e Windows 8.1, um [licença de desenvolvedor](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) deve ser instalado no dispositivo remoto.
    - Para dispositivos Windows 10, você deve habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development). 
  
-   Para PCs com Windows 10 que executam uma versão anterior à atualização do criador do Windows 10 do Windows 10, você deve instalar e executar os componentes de depuração remota.
  
-   Você deve ser um administrador do dispositivo remoto para configurar o firewall durante a instalação. Você deve ter acesso de usuário ao dispositivo remoto para executar o depurador remoto ou conectar-se a ele.  
  
##  <a name="BKMK_Security"></a>Segurança  
 Por padrão, o depurador remoto usa a Autenticação do Windows.  
  
> [!WARNING]
>  Você também pode optar por executar o depurador remoto no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo não há nenhuma segurança de rede. Escolha o Modo Sem Autenticação somente se você tiver certeza de que a rede não corre risco de tráfego mal-intencionado ou hostil.  
  
##  <a name="BKMK_DirectConnect"></a>Como conectar-se diretamente a um dispositivo remoto  
 Para se conectar diretamente a um dispositivo remoto, conecte o computador com o Visual Studio ao dispositivo usando um cabo Ethernet padrão. Se o dispositivo não tiver uma porta Ethernet, você poderá usar um adaptador USB-Ethernet para se conectar ao cabo.  
  
## <a name="BKMK_download"></a>Baixe e instale as ferramentas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a>Configurar o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]
  
##  <a name="BKMK_ConnectVS"></a>Configurando o projeto do Visual Studio para depuração remota  
 Você especifica o dispositivo remoto ao qual deseja se conectar nas propriedades do projeto. O procedimento varia dependendo da linguagem de programação. Você pode digitar o nome da rede do dispositivo remoto ou pode selecioná-lo na caixa de diálogo Selecionar Conexão de Depurador Remoto.  
  
 ![Marque a caixa de diálogo Conexão de depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 A caixa de diálogo lista somente os dispositivos que estão na sub-rede local do computador com o Visual Studio e que estão executando o depurador remoto.  
  
> [!TIP]
>  Se você tiver problemas para se conectar a um dispositivo remoto, tente inserir o endereço IP do dispositivo. Para determinar o endereço IP de um dispositivo, abra uma janela de comando e digite **ipconfig**. O endereço IP é listado como **endereço IPv4**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>Escolhendo o dispositivo remoto para projetos c# e Visual Basic  
 ![Gerenciado propriedades do projeto para a depuração remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Selecione o nome do projeto no Gerenciador de soluções e escolha **propriedades** no menu de atalho.  
  
2.  Selecione **depurar**.  
  
3.  Escolha **máquina remota** do **dispositivo de destino** lista.  
  
4.  Digite o nome de rede do dispositivo remoto no **máquina remota** caixa ou escolha **localizar** para escolher o dispositivo do **Selecionar Conexão de depurador remoto** caixa de diálogo.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a>Escolhendo o dispositivo remoto para projetos em JavaScript e C++  
 ![C &#43; &#43; Propriedades de depuração remota do projeto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Selecione o nome do projeto no Gerenciador de soluções e escolha **propriedades** no menu de atalho.  
  
2.  Expanda o **propriedades de configuração** nó e, em seguida, selecione **depuração**.  
  
3.  Escolha **depurador remoto** do **depurador a iniciar** lista.  
  
4.  Digite o nome de rede do dispositivo remoto no **nome da máquina** caixa ou clique na seta para baixo na caixa para escolher o dispositivo a partir de **Selecionar Conexão de depurador remoto** caixa de diálogo.  
  
##  <a name="BKMK_RunRemoteDebug"></a>Executando uma sessão de depuração remota  
 Você inicia e interrompe uma sessão de depuração remota e navega por ela da mesma maneira que faz em uma sessão local. Antes de iniciar a depuração, verifique se o Monitor de Depuração Remota está em execução no dispositivo remoto.  
  
 Em seguida, escolha **iniciar depuração** no **depurar** menu (teclado: F5). O projeto é recompilado, depois é implantado e iniciado no dispositivo remoto. O depurador suspende a execução em pontos de interrupção, e você pode fazer step-into, step-over e step-out do seu código. Escolha **parar depuração** para encerrar a sessão de depuração e fechar o aplicativo remoto. Para obter mais informações, consulte [depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Testando aplicativos UWP com o Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)