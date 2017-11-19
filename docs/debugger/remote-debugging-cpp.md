---
title: "Um projeto do Visual C++ de depuração remota | Microsoft Docs"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09bd8bc648b87f69720468afcdeefa1d16dd36f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Um projeto do Visual C++ no Visual Studio de depuração remota
Para depurar um aplicativo do Visual Studio em um computador diferente, instalar e executar as ferramentas remotas no computador onde você implantará o aplicativo, configure seu projeto para se conectar ao computador remoto do Visual Studio e, em seguida, implantar e executar seu aplicativo.

![Componentes do depurador remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Para obter informações sobre aplicativos de Windows Universal (UWP) a depuração remota, consulte [depurar um pacote de aplicativos instalado](debug-installed-app-package.md).

## <a name="requirements"></a>Requisitos

O depurador remoto é suportado no Windows 7 e versões mais recentes (não phone) e versões do Windows Server, iniciando com o Windows Server 2008 Service Pack 2. Para obter uma lista completa dos requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Não há suporte para a depuração entre dois computadores conectados por meio de um proxy. Depuração em uma conexão de baixa largura de banda, como dial-up da Internet, ou de alta latência, ou pela Internet entre países não é recomendado e pode falhar ou ser muito lento.
  
## <a name="download-and-install-the-remote-tools"></a>Baixe e instale as ferramentas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> Em alguns cenários, pode ser mais eficiente para executar o depurador remoto de um compartilhamento de arquivos. Para obter mais informações, consulte [executar o depurador remoto de um compartilhamento de arquivo](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a>Configurar o depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisa adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_cplusplus"></a>Depuração remota um projeto do Visual C++  
 No procedimento a seguir, o nome e caminho do projeto é C:\remotetemp\MyMfc e o nome do computador remoto é **MJO DL**.  
  
1.  Criar um aplicativo MFC chamado **mymfc.**  
  
2.  Definir um ponto de interrupção em algum lugar no aplicativo que facilmente for atingido, por exemplo, em **MainFrm.cpp**, no início de `CMainFrame::OnCreate`.  
  
3.  No Gerenciador de soluções, clique com botão direito no projeto e selecione **propriedades**. Abra o **depuração** guia.  
  
4.  Definir o **depurador a iniciar** para **Remote Windows Debugger**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Faça as seguintes alterações nas propriedades:  
  
    |Configuração|Valor|
    |-|-|  
    |Comando remoto|C:\remotetemp\mymfc.exe|  
    |Diretório de trabalho|C:\remotetemp|  
    |Nome do servidor remoto|MJO-DL:*portnumber*|  
    |Conexão|Remoto sem Autenticação do Windows|  
    |Tipo de Depurador|Somente Nativo|  
    |Diretório de implantação|C:\remotetemp.|  
    |Arquivos adicionais a implantar|C:\data\mymfcdata.txt.|  
  
     Se você implantar arquivos adicionais (opcionais), a pasta deve existir nos dois computadores.  
  
6.  No Gerenciador de soluções, clique com botão direito a solução e escolha **do Configuration Manager**.  
  
7.  Para o **depurar** configuração, selecione o **implantar** caixa de seleção.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Iniciar a depuração (**Depurar > Iniciar depuração**, ou **F5**).  
  
9. O executável é implantado automaticamente ao computador remoto.  
  
10. Se solicitado, insira as credenciais de rede para se conectar ao computador remoto.  
  
     As credenciais necessárias são específicas para a configuração de segurança da sua rede. Por exemplo, em um computador de domínio, você pode escolher um certificado de segurança ou inserir seu nome de domínio e senha. Em um computador de fora do domínio, insira o nome do computador e um nome de conta de usuário válido, como  **MJO-DL\name@something.com** , junto com a senha correta.  
  
11. No computador do Visual Studio, você verá que a execução é interrompida no ponto de interrupção.  
  
    > [!TIP]
    >  Como alternativa, você pode implantar os arquivos como uma etapa separada. No **Gerenciador de soluções,** com o botão direito do **mymfc** nó e, em seguida, escolha **implantar**.  
  
 Se você tiver arquivos de código não precisam ser usados pelo aplicativo, você precisa incluí-las no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais (da **Solution Explorer**, clique em **Adicionar > nova pasta**.) Em seguida, adicionar os arquivos na pasta (no **Solution Explorer**, clique em **Adicionar > Item existente**, em seguida, selecione os arquivos). Sobre o **propriedades** para cada arquivo, defina **copiar para diretório de saída** para **copiar sempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurar a depuração com símbolos remotos 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)   
 [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Depuração Remota de ASP.NET em um computador remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)