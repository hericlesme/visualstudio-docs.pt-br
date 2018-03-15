---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 37963e1ee5b7eeb0d07c36e0abe42c98eb6436fe
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
1. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **publicar** (para formulários da Web, **Publicar Web App**).

2. No **publicar** caixa de diálogo, selecione **pasta**, clique em **procurar**e crie uma nova pasta, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Para um aplicativo de Web Forms, escolha **personalizado** na caixa de diálogo Publicar, insira um nome de perfil e escolha **Okey**.

3. Clique em **Publicar**.

    O Visual Studio publica o projeto para a pasta. Mostra progresso na janela de saída.

4. No **publicar** caixa de diálogo, clique o **configurações** link e, em seguida, selecione o **configurações** guia.

5. Defina a configuração como **depurar**, selecione **excluir todos os arquivos existentes antes de publicar**e, em seguida, clique em **salvar**.

    > [!NOTE]
    > Se você usar uma compilação de versão, você desabilitar depuração no arquivo Web. config quando você publicar.

6. Clique em **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    O aplicativo publica um **depurar** configuração do projeto para a pasta local.

5. Copiar o diretório do projeto ASP.NET do computador do Visual Studio para o diretório local configurado para o aplicativo ASP.NET (neste exemplo, **C:\Publish**) no computador do servidor do Windows. Neste tutorial, vamos supor que você está copiando manualmente, mas você pode usar outras ferramentas, como o PowerShell, Xcopy ou Robocopy.

    > [!CAUTION]
    >  Se você precisar fazer alterações no código ou recompilação, você deve republicar e repita esta etapa. O executável que você copiou para o computador remoto deve corresponder exatamente, seu local de origem e símbolos.    Se você não fizer isso, você receberá um `cannot find or open the PDB file` aviso no Visual Studio quando você tentar depurar o processo.

6. No Windows Server, verifique se que você pode executar o aplicativo corretamente abrindo o aplicativo em seu navegador.

    Se o aplicativo não funcionar corretamente, pode haver uma incompatibilidade entre a versão do ASP.NET instalada no seu servidor e o computador com Visual Studio, ou pode haver um problema com a configuração do IIS ou o site da Web. Verifique novamente as etapas anteriores.
