---
title: Depurar um pacote de aplicativo instalado (UWP) | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 354c574a890ae0385a58594a22b3314a13b9d6b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Depurar um pacote de aplicativo instalado no Visual Studio (UWP)

Você pode depurar qualquer pacote de aplicativo instalado clicando **Depurar > outros destinos de depuração > Depurar pacote do aplicativo instalado**. Esse método de depuração está disponível para aplicativos de Windows Universal (UWP) nesses dispositivos:

* Windows 10 (sem suporte em telefones)
* XBox
* HoloLens
* IoT

Para obter mais informações sobre esses recursos, consulte o postagem de blog sobre atualizações para [depuração instalado pacotes de aplicativos](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) e o post em [criando aplicativos de Windows Universal (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Depurar um pacote do aplicativo instalado ou o aplicativo em execução em um dispositivo ou computador Local

1. Com o seu projeto UWP aberto no Visual Studio, clique em **Depurar > outros destinos de depuração > Depurar pacote do aplicativo instalado**.

2. Selecione **Máquina Local** ou **dispositivo**.

     Se você escolher **dispositivo**, seu computador deve estar conectado fisicamente em um dispositivo Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Em execução no momento instalado o aplicativo pacotes aparecem sob o **executando** nó. Instalado pacotes de aplicativos que não estão em execução Mostrar em **não está em execução**.

3. Selecione o nome do aplicativo que você deseja depurar em **executando** ou **não está em execução** e escolha **iniciar** ou, se o aplicativo já está em execução, escolha **Attach**.

     Se você selecionar **não iniciar, mas depurar meu código quando iniciar**, isso fará com que o depurador do Visual Studio anexar ao seu aplicativo quando você iniciá-lo em um momento personalizado. Essa é uma maneira eficiente para depurar os caminhos de controle de [inicialização diferentes métodos](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como a ativação de protocolo com parâmetros personalizados.

> [!NOTE]
> O Visual Studio também pode anexar a qualquer processo em execução do aplicativo UWP selecionando **depurar**e, em seguida, **anexar ao processo**. Anexar a um processo em execução não exige o projeto original do Visual Studio, mas ao carregar os símbolos do processo ajudará significativamente ao depurar um processo que você não tem o código original.
  
## <a name="remote"></a>Depurar um aplicativo instalado ou em execução em um computador remoto 

Quando você depura um pacote de aplicativos instalados em um computador remoto pela primeira vez, o Visual Studio instala a versão correta das ferramentas remotas para o seu dispositivo de destino. Seu dispositivo de destino deve ser um computador com Windows 10, o dispositivo XBox, HoloLens e IoT.

1. No seu dispositivo Windows 10, habilite [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development).

2. Se você estiver se conectando a um computador remoto executando a versão de atualização do pré-criador do Windows 10, primeiro manualmente [instalar e iniciar o depurador remoto](../debugger/remote-debugging.md).

     Para um dispositivo XBox, HoloLens e IoT e dispositivos do Windows que executam a atualização do criador do Windows 10, você não precisa instalar manualmente o depurador remoto. As ferramentas remotas serão instaladas automaticamente quando você implantar o aplicativo.

3. Clique em **Depurar > outros destinos de depuração > Depurar pacote do aplicativo instalado**.

4. Na primeira lista suspensa, escolha **máquina remota**.

5. Digite o nome ou endereço IP do computador que você deseja anexar.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Se você não conseguir conectar usando o nome do computador (depois que você escolher **iniciar**), use o endereço IP em vez disso. Use o endereço IP para XBox, HoloLens e IoT dispositivos.

5. Escolha como autenticar selecionando uma opção em **modo de autenticação**.

    Para a maioria dos aplicativos, mantenha o valor padrão, **Universal (protocolo não criptografado)**.

6. Selecione o nome do aplicativo que você deseja depurar em **executando** ou **não está em execução** e escolha **iniciar** ou (para aplicativos em execução) **Attach**.

     Se você selecionar **não iniciar, mas depurar meu código quando iniciar**, isso fará com que o depurador do Visual Studio anexar ao seu pacote de aplicativo quando você iniciá-lo em um momento personalizado. Essa é uma maneira eficiente para depurar os caminhos de controle de [inicialização diferentes métodos](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como a ativação de protocolo com parâmetros personalizados.

     Quando você depura um pacote de aplicativo instalado em um dispositivo conectado XBox, HoloLens e IoT pela primeira vez, o Visual Studio instala a versão correta do depurador remoto do seu dispositivo de destino. Isso pode demorar um pouco de tempo e você verá uma mensagem ``Starting remote debugger`` enquanto isso está acontecendo.

     > [!NOTE]
> Ao apresentar um XBox ou dispositivo HoloLens reiniciará o aplicativo com o depurador anexado se ele já está em execução.

> [!NOTE]
> Aplicativos UWP podem ser desenvolvidos e compilado no Windows 8.1 ou posterior, mas requerem o Windows 10 executar. Se você estiver desenvolvendo um aplicativo UWP em um computador do Windows 8.1, você pode depurar remotamente um aplicativo UWP em execução em outro dispositivo Windows 10, desde que o computador de host e de destino estão na mesma rede local. Para fazer isso, baixe e instale as ferramentas remotas para Visual Studio em ambos os computadores. A versão instalada deve corresponder à versão existente do Visual Studio que você instalou e a arquitetura que você selecionar (x86, x64) também deve corresponder para que seu aplicativo de destino.
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)  
 [Depuração remota](../debugger/remote-debugging.md)  
 [Configurar o Firewall do Windows para Depuração Remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)