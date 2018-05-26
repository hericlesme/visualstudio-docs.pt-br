---
title: Implantar na pasta local
description: Implantar um aplicativo em uma pasta local
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2018
---
1. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **publicar** (para formulários da Web, **Publicar Web App**).

    Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **novo perfil**.

1. No **publicar** caixa de diálogo, selecione **pasta**, clique em **procurar**e crie uma nova pasta, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Para um aplicativo de Web Forms, escolha **personalizado** na caixa de diálogo Publicar, insira um nome de perfil e escolha **Okey**.

1. Clique em **criar perfil** na lista suspensa (**publicar** é o valor padrão).

1. No **publicar** caixa de diálogo, clique o **configurações** link e, em seguida, selecione o **configurações** guia.

1. Defina a configuração como **depurar**, selecione **excluir todos os arquivos existentes antes de publicar**e, em seguida, clique em **salvar**.

    > [!NOTE]
    > Se você usar uma compilação de versão, você desabilitar depuração no arquivo Web. config quando você publicar.

1. Clique em **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    O aplicativo publica um **depurar** configuração do projeto para a pasta local. Mostra progresso na janela de saída.

1. Copiar o diretório do projeto ASP.NET do computador do Visual Studio para o diretório local configurado para o aplicativo ASP.NET (neste exemplo, **C:\Publish**) no computador do servidor do Windows. Neste tutorial, vamos supor que você está copiando manualmente, mas você pode usar outras ferramentas, como o PowerShell, Xcopy ou Robocopy.

    > [!CAUTION]
    >  Se você precisar fazer alterações no código ou recompilação, você deve republicar e repita esta etapa. O executável que você copiou para o computador remoto deve corresponder exatamente, seu local de origem e símbolos.    Se você não fizer isso, você receberá um `cannot find or open the PDB file` aviso no Visual Studio quando você tentar depurar o processo.

1. No Windows Server, verifique se que você pode executar o aplicativo corretamente abrindo o aplicativo em seu navegador.

    Se o aplicativo não funcionar corretamente, pode haver uma incompatibilidade entre a versão do ASP.NET instalada no seu servidor e o computador com Visual Studio, ou pode haver um problema com a configuração do IIS ou o site da Web. Verifique novamente as etapas anteriores.
