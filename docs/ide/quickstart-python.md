---
title: "Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Web Python | Microsoft Docs"
description: "Uma breve introdução ao uso de Python no Visual Studio que compila um aplicativo Web simples usando a estrutura do Falcon."
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
dev_langs:
- python
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 9b45c694399553dd262a68d821d1757b65ea9600
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Início rápido: Usar o Visual Studio para criar seu primeiro aplicativo Web Python

Nesta introdução de 5 a 10 minutos do IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo Web Python simples. Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.

## <a name="create-the-project"></a>Criar o projeto

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, escolha **Arquivo > Novo > Projeto...**.

1. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **Instalado** e selecione **Python**.

1. No painel central, escolha **Projeto Web**, nomeie o projeto como “HelloPython” e selecione **OK**.

    ![Caixa de diálogo Novo projeto com o projeto Web do Python selecionado](media/quickstart-python-00-web-project.png)

    Se os modelos de projeto Python não forem exibidos, cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas > Obter Ferramentas e Recursos...** para abrir o Instalador do Visual Studio. Escolha a carga de trabalho **Desenvolvimento de Python** e, em seguida, selecione **Modificar**.

    ![Carga de trabalho de desenvolvimento do Python no instalador do Visual Studio](../python/media/installation-python-workload.png)

1. O novo projeto será aberto no **Gerenciador de Soluções** no painel direito. O projeto está vazio neste momento porque ele não contém outros arquivos.

    ![Gerenciador de Soluções mostrando o projeto vazio recém-criado](media/quickstart-python-01-empty-project.png)

**Pergunta: qual é a vantagem de criar um projeto no Visual Studio para um aplicativo de Python?**

Resposta: os aplicativos Python costumam ser definidos usando somente arquivos e pastas, mas essa estrutura pode se tornar complexa conforme os aplicativos aumentam e talvez envolvem arquivos gerados automaticamente, JavaScript para aplicativos Web e assim por diante. Um projeto do Visual Studio ajuda a gerenciar essa complexidade. O projeto (um arquivo `.pyproj`) identifica todos os arquivos de origem e de conteúdo associados ao projeto, contém informações de build de cada arquivo, mantém as informações para a integração com sistemas de controle de código-fonte e ajuda a organizar o aplicativo em componentes lógicos.

## <a name="install-the-falcon-library"></a>Instalar a biblioteca Falcon

Aplicativos Web em Python quase sempre usam uma das muitas bibliotecas Python disponíveis para lidar com detalhes de baixo nível como o roteamento de solicitações da Web e formatação de respostas. Para essa finalidade, o Visual Studio fornece uma variedade de modelos para aplicativos Web usando as estruturas Bottle, Flask e Django.

Neste guia de início rápido, no entanto, você usará a biblioteca Falcon para realizar o processo de instalação de um pacote e de criação do aplicativo Web desde o início. (No momento, o Visual Studio não inclui modelos específicos do Falcon.) Para simplificar, as etapas a seguir instalam o Falcon no ambiente global padrão.

1. Expanda o nó **Ambiente do Python** no projeto para ver o ambiente padrão para o projeto.

    ![Gerenciador de soluções mostrando o ambiente padrão](media/quickstart-python-02-default-environment.png)

1. Clique com o botão direito do mouse no ambiente e selecione **Instalar pacote Python...**. Esse comando abre a janela **Ambientes de Python** na guia **Pacotes**. Insira “falcon” no campo de pesquisa e selecione **“pip install falcon” de PyPI**. Aceite os prompts de privilégios de administrador e observe o andamento na janela **Saída** janela no Visual Studio. (Um prompt para elevação é exibido quando a pasta de pacotes do ambiente global está localizada em uma área protegida como `c:\program files`.)

    ![Instalando a biblioteca Falcon](media/quickstart-python-03-install-package.png)

1. Uma vez instalada, a biblioteca aparece no ambiente em **Gerenciador de Soluções**, o que significa que você pode utilizá-la no código Python.

    ![Biblioteca Falcon instalada](media/quickstart-python-04-package-installed.png)

Para obter mais informações sobre o Falcon, visite [falconframework.org](https://falconframework.org/).

Observe que, em vez de instalar as bibliotecas no ambiente global, os desenvolvedores geralmente criam um “ambiente virtual” no qual instalar bibliotecas para um projeto específico. Muitos modelos de projeto de Python no Visual Studio incluem um arquivo `requirements.txt` que lista as bibliotecas das quais o modelo depende. Criando um projeto de um desses modelos dispara a criação de um ambiente virtual no qual as bibliotecas são instaladas. Para saber mais, confira [Usar ambientes virtuais](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments).

## <a name="add-a-code-file"></a>Adicionar um arquivo de código

Agora você está pronto para adicionar um pouco de código Python para implementar um aplicativo Web mínimo.

1. Clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Adicionar > Novo Item...**.

1. Na caixa de diálogo que aparece, selecione **Arquivo Python vazio**, nomeie-o como `hello.py` e selecione **Adicionar**. O Visual Studio abre o arquivo automaticamente em uma janela do editor. (Em geral, o comando **Adicionar > Novo item...** é uma ótima maneira de adicionar tipos diferentes de arquivos a um projeto, pois os modelos de item geralmente fornecem código clichê útil.)

1. Copie o código a seguir e cole-o em `hello.py`:

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. Depois que você colar esse código, o Visual Studio poderá mostrar um rabisco sob `falcon` na primeira linha e também sob `wsgiref.simple.server` na linha 20. Esses indicadores aparecem quando o Visual Studio ainda está criando o banco de dados do IntelliSense para esses módulos.

Para obter mais informações sobre Falcon, consulte o [Início rápido de Falcon](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Executar o aplicativo

1. Clique com o botão direito do mouse em `hello.py` no **Gerenciador de Soluções** e selecione **Definir como arquivo de inicialização**. O comando identifica o arquivo de código para iniciar em Python ao executar o aplicativo.

    ![Definir o arquivo de inicialização para um projeto no Gerenciador de Soluções](media/quickstart-python-05-set-as-startup-file.png)

1. Clique com o botão direito do mouse no projeto “Olá, Python” no **Gerenciador de Soluções** e selecione **Propriedades**. Selecione a guia **Depurar** e defina a propriedade **Número da porta** para `8080`. Essa etapa garante que o Visual Studio inicie um navegador com `localhost:8080` em vez de usar uma porta aleatória.

1. Selecione **Depurar > Iniciar Sem Depuração** (Ctrl+F5) para salvar as alterações nos arquivos e executar o aplicativo.

1. Aparece uma janela de comando com a mensagem “Iniciando servidor de aplicativo Web”, em seguida, uma janela do navegador deverá ser aberta para `localhost:8080`, exibindo a mensagem “Olá, Python!” A solicitação GET também aparece na janela de comando.

    Se um navegador não for aberto automaticamente, inicie o navegador de sua escolha e navegue até `localhost:8080`.)

    Caso apareça somente o shell interativo do Python na janela de comando ou se essa janela piscar brevemente na tela, verifique se você definiu `hello.py` como o arquivo de inicialização na etapa 1 acima.

1. Feche a janela de comando para interromper o aplicativo e, em seguida, feche a janela do navegador.

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este guia de início rápido, em que você aprendeu um pouco sobre o IDE do Visual Studio com Python. Para continuar com um tutorial mais completo sobre Python no Visual Studio, inclusive usando a janela interativa, depuração, visualização de dados e trabalhar com Git, selecione o botão abaixo.

> [!div class="nextstepaction"]
> [Tutorial: introdução ao Python no Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

- Saiba mais sobre os [Modelos de aplicativo Web Python no Visual Studio](../python/python-web-application-project-templates.md)
- Saiba mais sobre [Depuração de Python](../python/debugging-python-in-visual-studio.md)
- Saiba mais sobre o [IDE do Visual Studio](../ide/visual-studio-ide.md)
