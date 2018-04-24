---
title: Executar aplicativos UWP em um computador remoto | Microsoft Docs
ms.custom: ''
ms.date: 01/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2c09d29340584f3f6187175342fd1171dd59ba37
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Executar aplicativos UWP em um computador remoto no Visual Studio
  
Para executar um aplicativo UWP em um computador remoto, você deve anexar a ela usando as ferramentas remotas para Visual Studio. As ferramentas remotas permitem executar, depurar, analisar e testar um aplicativo UWP que está em execução em um dispositivo de um segundo computador que está executando o Visual Studio. Em execução em um dispositivo remoto pode ser especialmente eficaz quando o computador do Visual Studio não oferece suporte à funcionalidade específica para aplicativos UWP, como toque, localização geográfica e orientação física. Este tópico descreve os procedimentos para configurar e iniciar uma sessão remota.

Em alguns cenários, as ferramentas remotas são instaladas automaticamente quando você implanta em um dispositivo remoto.

- Para PCs com Windows 10 que executam os criadores de atualização e versões posteriores, ferramentas remotas serão instaladas automaticamente.
- Para dispositivos Windows 10 Xbox, IOT e HoloLens, ferramentas remotas serão instaladas automaticamente.
- Para Windows Mobile 10, você deve estar conectado fisicamente ao telefone, você deve habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development) e você deve selecionar **dispositivo** como o destino de depuração. Ferramentas remotas não são necessários ou suporte.

Para PCs com Windows 10 executando a versão de atualização de um pre-do criador do Windows, você deve instalar as ferramentas remotas no computador remoto manualmente para poder depurar. Siga as instruções neste tópico. 
  
##  <a name="BKMK_Prerequisites"></a> Pré-requisitos  
 Para depurar em um dispositivo remoto:  
  
- O dispositivo remoto e o computador do Visual Studio devem conectados por uma rede ou conectados diretamente por meio de um cabo Ethernet ou USB. Não há suporte à depuração pela Internet.  

- Você deve habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development). 
  
- Para PCs com Windows 10 que executam uma versão anterior à atualização do criador do Windows 10 do Windows 10, você deve [instalar e executar os componentes de depuração remota](#BKMK_download).
  
##  <a name="BKMK_Security"></a> Segurança  
Por padrão, **Universal (protocolo não criptografado)** é usado no Windows 10. Agora esse protocolo deve ser usado somente em redes confiáveis. A conexão de depuração é vulnerável a usuários mal-intencionados que podem interceptar e alterar dados passados entre o desenvolvimento e o computador remoto.
  
> [!WARNING]
>  Há nenhuma segurança de rede quando você definir o modo de autenticação como **Universal (protocolo não criptografado)** ou **nenhum**. Escolha os modos somente se você tiver certeza de que a rede não está em risco de tráfego mal-intencionado ou hostil.  
  
##  <a name="BKMK_DirectConnect"></a> Como conectar-se diretamente usando um cabo USB 

No Windows 10, você pode implantar em um dispositivo USB conectado escolhendo **dispositivo** em vez de **máquina remota** como o destino de implantação (você pode fazer isso no **padrão** barra de ferramentas ou na página de propriedades de depuração).

##  <a name="BKMK_ConnectVS"></a> Configurar o projeto do Visual Studio para depuração remota  
 Você especifica o dispositivo remoto ao qual deseja se conectar nas propriedades do projeto. O procedimento varia dependendo da linguagem de programação. Você pode digitar o nome de rede do dispositivo remoto, ou você pode selecionar a partir de **Conexão remota** caixa de diálogo.  
  
 ![Marque a caixa de diálogo Conexão de depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 A caixa de diálogo lista somente os dispositivos que estão na sub-rede local do computador com o Visual Studio e que estão executando o depurador remoto.  
  
> [!TIP]
>  Se você tiver problemas para se conectar a um dispositivo remoto, tente inserir o endereço IP do dispositivo. Para determinar o endereço IP de um dispositivo, abra uma janela de comando e digite **ipconfig**. O endereço IP é listado como **endereço IPv4**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Escolha o dispositivo remoto para projetos c# e Visual Basic  
  
1.  Selecione o nome do projeto no Gerenciador de soluções e escolha **propriedades** no menu de atalho.  
  
2.  Selecione **depurar**.  
  
3.  Escolha **máquina remota** do **dispositivo de destino** lista.  
  
4.  Digite o nome de rede do dispositivo remoto no **máquina remota** caixa ou escolha **localizar** para escolher o dispositivo do **Selecionar Conexão de depurador remoto** caixa de diálogo. 

    ![Gerenciado propriedades do projeto para a depuração remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Escolha o dispositivo remoto para projetos em JavaScript e C++  
  
1.  Selecione o nome do projeto no Gerenciador de soluções e escolha **propriedades** no menu de atalho.  
  
2.  Expanda o **propriedades de configuração** nó e, em seguida, selecione **depuração**.  
  
3.  Escolha **depurador remoto** do **depurador a iniciar** lista.  
  
4.  Digite o nome de rede do dispositivo remoto no **nome da máquina** caixa ou clique na seta para baixo na caixa para escolher o dispositivo a partir de **Selecionar Conexão de depurador remoto** caixa de diálogo.  

    ![C&#43; &#43; propriedades para depuração remota do projeto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> Baixe e instale as ferramentas remotas (pré-criadores de atualização)

Se você estiver usando versões de atualização de uma versão anterior, criador Windows 10, siga estas instruções. Caso contrário, você poderá ignorar esta seção.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurar o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Iniciar uma sessão de depuração remota  
 Você inicia e interrompe uma sessão de depuração remota e navega por ela da mesma maneira que faz em uma sessão local. Em versões de atualização do pré-criador do Windows 10, verifique se que o Monitor de depuração remota está em execução no dispositivo remoto.  
  
 Em seguida, escolha **iniciar depuração** no **depurar** menu (teclado: F5). O projeto é recompilado, depois é implantado e iniciado no dispositivo remoto. O depurador suspende a execução em pontos de interrupção, e você pode fazer step-into, step-over e step-out do seu código. Escolha **parar depuração** para encerrar a sessão de depuração e fechar o aplicativo remoto.
  
## <a name="see-also"></a>Consulte também  
 [Opções de implantação remota avançadas](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Testando aplicativos UWP com o Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)