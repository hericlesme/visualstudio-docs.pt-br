A implantação da Web 3.6 para servidores de hospedagem fornece recursos adicionais de configuração que permitem a criação do arquivo publicar configurações de interface do usuário.

1. Se você tiver 3.6 implantar da Web que já está instalado no Windows Server, desinstalá-lo usando **painel de controle** > **programas** > **desinstalar um programa**.

1. Em seguida, instale 3.6 de implantação da Web para hospedar servidores no Windows Server.

    Para instalar a implantação da Web para servidores de hospedagem, use o [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para localizar o link do instalador de plataforma da Web do IIS, selecione **IIS** no painel esquerdo do Gerenciador do servidor. O servidor com o botão direito e selecione **serviços de informações da Internet (IIS) Manager**.)

    O Web Platform Installer, você encontrará **implantação da Web para hospedar servidores** na guia aplicativos.

1. Se você não tiver instalado já **ferramentas e Scripts de gerenciamento do IIS**, instale-o agora.

    Vá para **selecionar funções de servidor** > **servidor Web (IIS)** > **as ferramentas de gerenciamento**e, em seguida, selecione o **Scripts de gerenciamento do IIS e ferramentas** função, clique em **próxima**e, em seguida, instalar a função.

    ![Instalar ferramentas e Scripts de gerenciamento do IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Os scripts e ferramentas são necessárias para habilitar a geração de arquivo de configurações de publicação.

1. (Opcional) Verificar a implantação da Web está executando corretamente abrindo **painel de controle > sistema e segurança > Ferramentas administrativas > serviços** e certifique-se de que **serviço de agente de implantação da Web** está em execução (o nome do serviço é diferente em versões mais antigas).

    Se o serviço de agente não está em execução, inicie-o. Se não estiver presente em todos os, acesse **painel de controle > Programas > desinstalar um programa**, localize **Microsoft Web Deploy <version>** . Escolher **alteração** a instalação e certifique-se de que você escolhe **será instalado na unidade de disco rígido local** para os componentes de implantação da Web. Conclua as etapas de instalação de alteração.