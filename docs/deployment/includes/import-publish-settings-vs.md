
1. No computador em que o projeto ASP.NET aberto no Visual Studio, clique com botão direito no projeto no Gerenciador de soluções e escolha **publicar**.

1. Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **criar novo perfil**.

1. No **escolher um destino de publicação** caixa de diálogo, clique em **importar perfil**.

    ![Escolher publicar](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue até o local do arquivo de configurações de publicação que você criou na seção anterior.

1. No **importar o arquivo de configurações de publicação** caixa de diálogo, navegue até e selecione o perfil que você criou na seção anterior e clique em **abrir**.

    O Visual Studio inicia o processo de implantação e a janela de saída mostra o progresso e os resultados.

    Se você obtiver uma implantação de quaisquer erros, clique em **configurações** para editar as configurações. Modificar as configurações e clique em **validar** para testar as novas configurações. Se o nome do host não for encontrado, tente o endereço IP em vez do nome de host no **servidor** e **URL de destino** campos.

    ![Editar as configurações na ferramenta de publicação](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
