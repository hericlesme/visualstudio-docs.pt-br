---
title: Depurar um pacote do aplicativo instalado (UWP) | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 6bb43288b7e5a4dd9241a7492baeed9de1c49890
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059226"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Depurar um pacote do aplicativo instalado no Visual Studio (UWP)

Você pode depurar qualquer pacote de aplicativo instalado clicando **Depurar > outros destinos de depuração > Depurar pacote do aplicativo instalado**. Esse método de depuração está disponível para aplicativos Universal do Windows (UWP) nesses dispositivos:

* Windows 10 (sem suporte em telefones)
* XBox
* HoloLens
* IoT

Para obter mais informações sobre esses recursos, consulte o postagem no blog sobre atualizações para [depuração instalado pacotes de aplicativos](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) e a postagem no [criação de aplicativos Universal do Windows (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Depurar um pacote do aplicativo instalado ou o aplicativo em execução em um dispositivo ou computador Local

1. Com o seu projeto UWP aberto no Visual Studio, clique em **Depurar > outros destinos de depuração > Depurar pacote do aplicativo instalado**.

2. Selecione a **computador Local** ou **dispositivo**.

     Se você escolher **dispositivo**, seu computador deve estar fisicamente conectado a um dispositivo Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Em execução no momento instalado o aplicativo pacotes apareçam sob o **executando** nó. Instalado pacotes de aplicativos que não estão em execução Mostrar backup sob **não está em execução**.

3. Selecione o nome do aplicativo que você deseja depurar sob **em execução** ou **não está em execução** e escolha **iniciar** ou, se o aplicativo já está em execução, escolha **anexar**.

     Se você selecionar **não iniciar, mas depurar meu código quando iniciar**, isso fará com que o depurador do Visual Studio para anexar ao seu aplicativo quando você iniciá-lo em um tempo personalizado. Isso é uma maneira eficiente para depurar os caminhos de controle de [métodos de inicialização diferente de](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como a ativação de protocolo com parâmetros personalizados.

> [!NOTE]
> Visual Studio também pode anexar a qualquer processo de aplicativo UWP em execução, selecionando **Debug**e então **anexar ao processo**. Anexando a um processo em execução não exige que o projeto original do Visual Studio, mas o carregamento de símbolos do processo ajudará a significativamente durante a depuração de um processo que você não tiver o código original para.
  
## <a name="remote"></a> Depurar um aplicativo instalado ou em execução em um computador remoto 

Quando você depura um pacote de aplicativos instalados em um computador remoto pela primeira vez, o Visual Studio instala a versão correta das ferramentas remotas para o seu dispositivo de destino. Seu dispositivo de destino deve ser um computador com Windows 10, o dispositivo IoT, HoloLens ou XBox.

1. No seu dispositivo Windows 10, habilite [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development).

2. Se você estiver se conectando a um computador remoto executando versão de atualização do pre-criador do Windows 10, primeiro manualmente [instalar e iniciar o depurador remoto](../debugger/remote-debugging.md).

     Para um dispositivo de IoT, HoloLens ou XBox e dispositivos do Windows que executam o Update Windows 10 Creators, você não precisa instalar manualmente o depurador remoto. As ferramentas remotas serão instaladas automaticamente quando você implanta o aplicativo.

3. Clique em **Depurar > outros destinos de depuração > Depurar pacote do aplicativo instalado**.

4. Na primeira lista suspensa, escolha **computador remoto**.

5. Digite o nome ou endereço IP do computador que deseja anexar.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Se você não conseguir conectar usando o nome do computador (depois de escolher **iniciar**), use o endereço IP em vez disso. Use o endereço IP para os dispositivos de IoT, HoloLens ou XBox.

5. Escolha como autenticar, selecionando uma opção no **modo de autenticação**.

    Para a maioria dos aplicativos, mantenha o valor padrão, **Universal (protocolo não criptografado)**.

6. Selecione o nome do aplicativo que você deseja depurar sob **em execução** ou **não está em execução** e escolha **iniciar** ou (para aplicativos em execução) **Attach**.

     Se você selecionar **não iniciar, mas depurar meu código quando iniciar**, isso fará com que o depurador do Visual Studio anexar ao seu pacote do aplicativo quando você iniciá-lo em um tempo personalizado. Isso é uma maneira eficiente para depurar os caminhos de controle de [métodos de inicialização diferente de](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como a ativação de protocolo com parâmetros personalizados.

     Quando você depura um pacote de aplicativos instalados em um dispositivo do XBox, HoloLens ou IoT conectado pela primeira vez, o Visual Studio instala a versão correta do depurador remoto para seu dispositivo de destino. Isso pode demorar um pouco de tempo e você verá uma mensagem ``Starting remote debugger`` enquanto isso está acontecendo.

     > [!NOTE]
> No presente, um XBox ou dispositivo HoloLens reiniciará o aplicativo com o depurador anexado se ele já está em execução.

Para obter informações sobre opções avançadas para a implantação remota de aplicativos UWP, consulte [UWP apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) implantação e depuração. 
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)  
 [Depuração remota](../debugger/remote-debugging.md)  
 [Configurar o Firewall do Windows para Depuração Remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)