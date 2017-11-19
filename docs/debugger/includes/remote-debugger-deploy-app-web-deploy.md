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
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
Se você instalou a implantação da Web usando o Web Platform Installer, você pode implantar o aplicativo diretamente do Visual Studio.

1. Inicie o Visual Studio com privilégios de administrador e, em seguida, reabra o projeto.

    São necessários privilégios de administrador para implantar seu aplicativo usando a implantação da Web.

2. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **publicar**.

3. Para **selecionar um destino de publicação**, selecione **IIS, FTP, etc.** e clique em **publicar**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. Insira os parâmetros de configuração de correção para a instalação do IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se um nome de host não resolver ao tentar validar na próxima etapas no **Server** texto caixa, tente o endereço IP. Incluir `http://` como um prefixo de **Server** campo.  Verifique se você usa a porta 80 no **Server** texto caixa e certifique-se de que a porta 80 está aberta no firewall.

6. Clique em **próximo**, escolha um **depurar** configuração e escolha **remover arquivos adicionais no destino** sob o **Publicar arquivo** Opções.

    > [!NOTE]
    > Se você escolher uma configuração de versão, você desabilitar depuração no arquivo Web. config quando você publicar.

5. Clique em **Prev**e, em seguida, escolha **validar**. Se a configuração de conexão for validado, você pode tentar publicar.

6. Clique em **publicar** para publicar o aplicativo.

    A guia saída mostra se a publicação foi bem-sucedida e o navegador abre o aplicativo.

    Se você receber um erro mencionar a implantação da Web, verifique novamente as etapas de instalação de implantação da Web e verifique se as portas corretas estão abertas (também implantação da Web requer a porta 8172 sejam abertos no servidor).

    Se o aplicativo implanta com êxito, mas não funcionar corretamente, pode haver um problema com a configuração do IIS, a instalação do ASP.NET ou sua configuração de site da Web. No Windows Server, abra o site da Web do IIS para mensagens de erro mais específicas e, em seguida, verifique novamente as etapas anteriores.