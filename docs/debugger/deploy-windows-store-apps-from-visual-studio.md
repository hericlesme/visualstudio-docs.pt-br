---
title: Implantar aplicativos UWP do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 95f009ca761d4d978fb5e5a9323722e5dfc34cb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Implantar aplicativos UWP do Visual Studio
![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 A funcionalidade de implantação do Visual Studio compila e registra aplicativos da UWP que são criados com o Visual Studio em um dispositivo de destino. Exatamente como o aplicativo é registrado depende de o dispositivo de destino ser local ou remoto:  
  
-   Quando o destino é o computador local com o Visual Studio, ele registra o aplicativo de sua pasta de build.  
  
-   Quando o destino é um dispositivo remoto, o Visual Studio copia os arquivos necessários ao computador remoto e registra o aplicativo nesse dispositivo.  
  
 Implantação é automática quando você depura seu aplicativo do Visual Studio usando o **iniciar depuração** opção (teclado: F5) ou o **Start Without Debugging** opção (teclado: CTRL + F5). Você também pode implantar seu aplicativo manualmente. A implantação manual é útil nos seguintes cenários:  
  
-   Teste ad-hoc em um computador local ou remoto.  
  
-   Implantação de um aplicativo que iniciará outro aplicativo que você quer depurar.  
  
-   Implantação de um aplicativo que será depurado quando é iniciado por outro aplicativo ou método.
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Como implantar um aplicativo UWP  
 Implantar manualmente um aplicativo é simples:  
  
1.  Se você está implantando para um dispositivo remoto, especifique o nome ou o endereço IP do dispositivo na página de propriedade do projeto de inicialização do aplicativo. (As etapas para fazer isso são listadas a seguir neste tópico.)  
  
2.  Na barra de ferramentas do depurador Visual Studio, escolha o destino de implantação na lista suspensa ao lado de **iniciar depuração** botão.  
  
     ![Executar na máquina Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  Sobre o **criar** menu, escolha **implantar**  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a>Como especificar um dispositivo remoto  

**Pré-requisitos**  
  
Em um dispositivo remoto Windows 10, você deve habilitar [modo de desenvolvedor](/windows/uwp/get-started/enable-your-device-for-development). Em dispositivos Windows 10 que executam a atualização do criador ou posterior, as ferramentas remotas são instaladas automaticamente quando você implantar seu aplicativo. Para obter mais informações, consulte [depurar um pacote de aplicativos instalados](../debugger/debug-installed-app-package.md).

> [!NOTE]
> No Windows 8.1 e versões de atualização do pré-criador do Windows 10, as ferramentas remotas para Visual Studio deve ser instaladas no dispositivo remoto e o depurador remoto deve estar em execução. No Windows 8.1, você também deve instalar uma licença de desenvolvedor.
  
A implantação usa o canal de rede do depurador remoto para enviar os arquivos do aplicativo ao dispositivo remoto.  
  
#### <a name="to-specify-a-remote-device"></a>Para especificar um dispositivo remoto  
  
1.  Na página de propriedade de depuração do projeto de inicialização, especifique o nome ou o endereço IP de um destino de implantação remoto.  
  
2.  Para abrir a página de propriedades de depuração, escolha o projeto no Gerenciador de soluções e escolha **propriedades** no menu de atalho.  
  
3.  Em seguida, escolha o **depurar** nó na janela de páginas de propriedade.

4. Para **dispositivo de destino**, selecione **máquina remota**.

5. Em **máquina remota**, clique em **localizar**.
  
4.  Você pode digitar o nome ou endereço IP do dispositivo remoto, ou você pode escolher o dispositivo a partir de **Conexão remota** caixa de diálogo.  
  
     ![Marque a caixa de diálogo Conexão de depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     O **Conexão remota** caixa de diálogo exibe os dispositivos na sub-rede local e em qualquer dispositivo que está conectado diretamente ao computador do Visual Studio por um cabo Ethernet.  
  
 **Especificar o dispositivo remoto em uma página de projeto de JavaScript ou Visual C++**  
  
 ![C &#43; &#43; Propriedades de depuração remota do projeto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Escolha **depurador remoto** do **depurador a iniciar** lista.  
  
2.  Digite o nome de rede do dispositivo remoto no **nome da máquina** caixa. Ou então, você pode escolher a seta para baixo na caixa para selecionar o dispositivo da caixa de diálogo Selecionar Conexão de Depurador Remoto.  
  
 **Especificar o dispositivo remoto em uma página de projeto do Visual c# e Visual Basic**  
  
 ![Gerenciado propriedades do projeto para a depuração remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Escolha **máquina remota** do **dispositivo de destino** lista.  
  
2.  Digite o nome de rede do dispositivo remoto no **máquina remota** caixa ou clique em **localizar** para escolher o dispositivo do **Selecionar Conexão de depurador remoto** caixa de diálogo.  
  
##  <a name="BKMK_Deployment_options"></a>Opções de implantação  
 Você pode definir as opções de implantação a seguir na página de propriedade de depuração do projeto de inicialização.  
  
 **Permitir Loopback de rede**  
 Por motivos de segurança, um UWP ou [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativo instalado da maneira padrão não tem permissão para fazer chamadas de rede para o dispositivo está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], você deve testá-lo sem a isenção.  
  
 Para remover a isenção de loopback de rede do aplicativo:  
  
-   Na página de propriedade de depuração c# e VB, desmarque o **permitir Loopback de rede** caixa de seleção.  
  
-   Na página de propriedade de JavaScript e depuração, defina o **permitir Loopback de rede** valor **não**.  
  
 **Não iniciar, mas depurar meu código quando ele iniciar (c# e VB) / Iniciar aplicativo (JavaScript e C++)**  
 Para configurar a implantação para iniciar automaticamente uma sessão de depuração quando o aplicativo é iniciado:  
  
-   Na página de propriedade de depuração c# e VB, marque o **não iniciar, mas depurar meu código quando iniciar** caixa de seleção.  
  
-   Na página de propriedade de JavaScript e depuração, defina o **Iniciar aplicativo** valor **Sim**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar um pacote de aplicativos instalados](../debugger/debug-installed-app-package.md).   
 [Executar aplicativos do Visual Studio](../debugger/run-store-apps-from-visual-studio.md)