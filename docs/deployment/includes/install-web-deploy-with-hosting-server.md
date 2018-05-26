A implantação da Web 3.6 para servidores de hospedagem fornece recursos de configuração adicionais que permitem a criação de um arquivo de configurações publicar de interface do usuário.

1. Se você tiver 3.6 implantar Web que já está instalado no Windows Server, desinstalá-lo usando **painel de controle** > **programas** > **desinstalar um programa**.

1. Em seguida, instale o Web implantar 3.6 para servidores de hospedagem no Windows Server.

    Para instalar a implantação da Web para servidores de hospedagem, use o [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para localizar o link do instalador de plataforma da Web do IIS, selecione **IIS** no painel esquerdo do Gerenciador do servidor. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.)

    O Web Platform Installer, você encontrará **implantação da Web para servidores de hospedagem** na guia aplicativos.

1. Se você não instalou já **ferramentas e Scripts de gerenciamento do IIS**, instale-o agora.

    Vá para **selecionar funções de servidor** > **servidor Web (IIS)** > **ferramentas de gerenciamento**e, em seguida, selecione o **Scripts de gerenciamento do IIS Ferramentas e** função, clique em **próximo**e, em seguida, instalar a função.

    ![Instalar ferramentas e Scripts de gerenciamento do IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Os scripts e ferramentas são necessárias para habilitar a geração de arquivo de configurações de publicação.

1. (Opcional) Verificar se implantação da Web está funcionando corretamente abrindo **painel de controle > sistema e segurança > Ferramentas administrativas > serviços** e certifique-se de que **o serviço de agente de implantação Web** está em execução (a nome do serviço é diferente em versões mais antigas).

    Se o serviço de agente não está em execução, inicie-o. Se não estiver presente em todos os, vá para **painel de controle > Programas > desinstalar um programa**, localizar **Microsoft Web Deploy <version>** . Escolha a **alteração** a instalação e certifique-se de que você escolha **será instalado na unidade de disco rígido local** para os componentes de implantação da Web. Conclua as etapas de instalação de alteração.