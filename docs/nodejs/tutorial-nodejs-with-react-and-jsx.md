---
title: Criar um aplicativo Node.js e React – Visual Studio | Microsoft Docs
description: Neste tutorial, você cria um aplicativo Node.js e React no Visual Studio
ms.custom: mvc
ms.date: 02/19/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 21debd24f69b79cb2dbbf9e9ceea928ac9dd851e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Tutorial: Criar um aplicativo Node.js e React no Visual Studio
O Visual Studio permite criar facilmente um projeto de Node.js e aproveitar o IntelliSense e outros recursos internos que dão suporte a Node.js. Neste tutorial para Visual Studio, você cria um projeto de aplicativo Web Node.js de um modelo do Visual Studio. Em seguida, você cria um aplicativo simples usando o React.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Criar um projeto Node.js
> * Adicionar pacotes npm
> * Adicionar código React ao seu aplicativo
> * Transcompilar JSX
> * Anexar o depurador

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter o Visual Studio instalado e a carga de trabalho de desenvolvimento de Node.js.

    Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo projeto**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**.

* Você precisa ter o tempo de execução do Node.js instalado.

    Se não o tiver instalado, instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/). Em geral, o Visual Studio detecta automaticamente o tempo de execução do Node.js instalado. Se ele não detectar um tempo de execução instalado, você poderá configurar seu projeto para fazer referência ao tempo de execução instalado na página de propriedades (depois de criar um projeto, clique com botão direito do mouse no nó do projeto e escolha **Propriedades**).

    Este tutorial foi testado com a versão 8.9.4.

## <a name="create-a-project"></a>Criar um projeto
Primeiro, crie um projeto de aplicativo Web Node.js.

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.

1. Na caixa de diálogo **Novo projeto**, no painel esquerdo, expanda **JavaScript** e escolha **Node.js**. No painel central, escolha **Aplicativo Web Node.js em Branco**, digite o nome **NodejsWebAppBlank** e, em seguida, escolha **OK**.

     Se não vir o modelo de projeto **Aplicativo Web Node.js em Branco**, você deverá instalar a carga de trabalho de desenvolvimento do Node.js primeiro.

    O Visual Studio cria a nova solução e abre seu projeto.

    ![Projeto Node.js no Gerenciador de Soluções](../nodejs/media/tutorial-nodejs-react-project-structure.png)

    - O seu projeto está realçado em negrito, usando o nome que você forneceu na caixa de diálogo **Novo Projeto**. No sistema de arquivos, este projeto é representado por um arquivo *.njsproj* na pasta do projeto. Você pode definir propriedades e variáveis de ambiente associadas ao projeto clicando com o botão direito do mouse no projeto e escolhendo **Propriedades**. Você pode fazer o ciclo com outras ferramentas de desenvolvimento, uma vez que o arquivo de projeto não faz alterações personalizadas na fonte do projeto Node.js.

    - No nível superior está uma solução que, por padrão, tem o mesmo nome que o projeto. Uma solução, representada por um arquivo *.sln* no disco, é um contêiner para um ou mais projetos relacionados.

    - O nó de npm mostra os pacotes npm instalados. Você pode clicar com o botão direito do mouse no nó de npm para pesquisar e instalar pacotes de npm usando uma caixa de diálogo.

    - Arquivos de projeto como *server.js* aparecem no nó do projeto. *server.js* é o arquivo de inicialização do projeto.

## <a name="add-npm-packages"></a>Adicionar pacotes npm

Este aplicativo requer um número de módulos npm para ser executado corretamente.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. No Gerenciador de Soluções (painel direito), clique com botão direito do mouse no nó **npm** do projeto e escolha **Instalar Novos Pacotes npm**.

    Na caixa de diálogo **Instalar Novos Pacotes npm**, você pode optar por instalar a versão mais recente do pacote ou especificar uma versão. Se você optar por instalar a versão atual desses pacotes, mas tiver erros inesperados posteriormente, talvez seja necessário instalar as versões exatas do pacote descritas nas próximas etapas.

1. Na caixa de diálogo **Instalar Novos Pacotes npm**, pesquise pelo pacote react e clique em **Instalar Pacote** para instalá-lo.

    ![Instalar pacotes npm](../nodejs/media/tutorial-nodejs-react-install-packages.png)

    A janela **Saída** mostra o andamento da instalação do pacote. Quando instalado, o pacote é exibido sob o nó **npm**.

    O arquivo *package.json* do projeto é atualizado com as informações do novo pacote, incluindo a versão do pacote.

1. Em vez de usar a interface do usuário para pesquisar e adicionar o restante dos pacotes um de cada vez, cole o seguinte código em package.json. Substitua a seção `dependencies` por este código:

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.2.0",
      "react-dom": "16.2.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. Clique com botão direito do mouse no nó **npm** em seu projeto e escolha **Instalar Pacotes npm Ausentes**.

    A janela **Saída** mostra o andamento da instalação do pacote.

    Estes são os módulos npm que aparecem no Gerenciador de Soluções após a instalação.

    ![Pacotes npm](../nodejs/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Se você preferir instalar pacotes npm usando a linha de comando, clique com o botão direito do mouse no nó do projeto e escolha **Abrir Prompt de Comando Aqui**. Usar comandos padrão do Node.js para instalar pacotes.

## <a name="add-project-files"></a>Adicionar arquivos de projeto

Nestas etapas, você adiciona quatro novos arquivos ao seu projeto.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Para este aplicativo simples, você pode adicionar novos arquivos de projeto à raiz do projeto. (Na maioria dos aplicativos, normalmente você adiciona os arquivos a subpastas e ajusta adequadamente as referências do caminho relativo).

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto **NodejsWebAppBlank** e escolha **Adicionar** > **Novo Item**.

1. Na caixa de diálogo **Adicionar Novo Item**, escolha **Arquivo JSX TypeScript**, digite o nome *app.tsx* e clique em **OK**.

1. Repita essas etapas para adicionar *webpack-config.js*.

1. Repita as mesmas etapas para adicionar *index.html* ao projeto. Em vez de um arquivo JavaScript, escolha **Arquivo HTML**.

1. Repita as mesmas etapas para adicionar *tsconfig.json* ao projeto. Em vez de um arquivo JavaScript, escolha **Arquivo de Configuração JSON do TypeScript**.

## <a name="add-app-code"></a>Adicionar código do aplicativo

1. Abra *server.js* e substitua o código pelo seguinte:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   O código anterior usa o Express para iniciar o Node.js como seu servidor de aplicativos Web. Esse código define a porta como o número da porta configurado nas propriedades do projeto (por padrão, a porta é configurada como 1337 nas propriedades). Para abrir as propriedades do projeto, clique com o botão direito do mouse no Gerenciador de Soluções e escolha **Propriedades**.

1. Abra *app.tsx* e adicione o seguinte código:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    O código anterior usa a sintaxe JSX e o React para exibir uma mensagem simples.

1. Abra *index.html* e substitua a seção **body** pelo código a seguir:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Esta página HTML carrega *app-bundle.js*, que contém o código de JSX e React transcompilado para JavaScript simples. Atualmente, *app-bundle.js* é um arquivo vazio. Na próxima seção, você configura opções para transcompilar o código.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configurar webpack e opções do compilador TypeScript

Nas etapas anteriores, você adicionou *webpack-config.js* ao projeto. Em seguida, você adiciona o código de configuração do webpack. Você adicionará uma configuração de webpack simples que especifica um arquivo de entrada (*app.tsx*) e um arquivo de saída (*app-bundle.js*) para agrupar e transcompilar JSX para JavaScript simples. Para transcompilar, você também configura algumas opções do compilador TypeScript. Esse código é uma configuração básica que serve como uma introdução ao webpack e ao compilador TypeScript.

1. No Gerenciador de Soluções, abra *webpack-config.js* e adicione o código a seguir.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    O código da configuração de webpack instrui o Webpack a usar o carregador de TypeScript para transcompilar o JSX.

1. Abra tsconfig.json e adicione o código a seguir, que especifica as opções do compilador TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    app.tsx é especificado como o arquivo de origem.

## <a name="transpile-the-jsx"></a>Transcompilar o JSX

1. No Gerenciador de Soluções, clique com o botão direito do mouse no nó do projeto e escolha **Abrir Prompt de Comando Aqui**.

1. No prompt de comando, digite o seguinte comando:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    A janela do prompt de comando mostra o resultado.

    ![Execute o webpack](../nodejs/media/tutorial-nodejs-react-run-webpack.png)

    Se encontrar erros em vez da saída anterior, você precisará resolvê-para que seu aplicativo funcione. Se as versões de seu pacote npm forem diferentes das versões mostradas neste tutorial, isso poderá ser uma fonte de erros. Uma maneira de corrigir erros é usar as versões exatas mostradas nas etapas anteriores. Além disso, se uma ou mais dessas versões de pacote tiver sido preterida e gerar um erro, talvez você precise instalar uma versão mais recente para corrigir erros.

1. No Gerenciador de Soluções, clique com o botão direito do mouse no nó do projeto e escolha **Adicionar** > **Pasta Existente** e, em seguida, escolha a pasta *dist* e clique em **Selecione Pasta**.

    O Visual Studio adiciona a pasta *dist* ao projeto que contém *app-bundle.js* e *app-bundle.js.map*.

1. Abra *app-bundle.js* para ver o código JavaScript transcompilado.

1. Caso seja solicitado a recarregar arquivos modificados externamente, clique em **Sim para todos**.

    ![Carregar arquivos modificados](../nodejs/media/tutorial-nodejs-react-reload-files.png)

Cada vez que fizer alterações em *app.tsx*, você precisará executar novamente o comando webpack.

## <a name="run-the-app"></a>Executar o aplicativo

1. Certifique-se de que o Chrome seja selecionado como o destino de depuração atual.

    ![Selecione o Chrome como destino de depuração](../nodejs/media/tutorial-nodejs-react-debug-target.png)

1. Para executar o aplicativo, pressione **F5** (**Depurar** > **Iniciar Depuração**) ou no botão de seta verde.

    É aberta uma janela do console do Node.js mostrando a porta na qual o depurador está escutando.

    O Visual Studio inicia o aplicativo iniciando o arquivo de inicialização, *server.js*.

    ![Execute o React no navegador](../nodejs/media/tutorial-nodejs-react-running-react.png)

1. Feche a janela do navegador.

1. Feche a janela do console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Defina um ponto de interrupção e execute o aplicativo

1. Em *server.js*, clique na medianiz à esquerda da declaração `staticPath` para definir um ponto de interrupção:

    ![Definir um ponto de interrupção](../nodejs/media/tutorial-nodejs-react-set-breakpoint.png)

    Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não.

1. Para executar o aplicativo, pressione **F5** (**Depurar** > **Iniciar Depuração**).

    O depurador pausa no ponto de interrupção definido (a instrução atual é marcada em amarelo). Agora, você pode inspecionar o estado do aplicativo passando o mouse sobre as variáveis que estão no escopo, usando as janelas do depurador, como **Locais** e **Inspecionar**.

1. Pressione **F5** para continuar o aplicativo.

1. Se quiser usar as Ferramentas para Desenvolvedores do Chrome, pressione **F12**. Você pode usar essas ferramentas para examinar o DOM e interagir com o aplicativo usando o Console do JavaScript.

1. Feche o navegador da Web e o console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Defina e atinja um ponto de interrupção no código do React do lado do cliente

Na seção anterior, você anexou o depurador ao código do Node.js do lado do servidor. Para anexar o depurador do Visual Studio e atingir pontos de interrupção no código do React lado do cliente, o depurador precisa de ajuda para identificar o processo correto. Esta é uma maneira de permitir isso.

1. Feche todas as janelas do Chrome.

1. Abra o comando **Executar** do botão **Iniciar** do Windows (clique com o botão direito do mouse e escolha **Executar**) e digite o seguinte comando:

    `chrome.exe --remote-debugging-port=9222`

    Isso inicia o Chrome com a depuração habilitada.

1. Alterne para o Visual Studio e defina um ponto de interrupção no código *app-bundle.js* na função `render()`, conforme mostrado na ilustração a seguir:

    ![Definir um ponto de interrupção](../nodejs/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

1. Com o Chrome selecionado como destino de depuração no Visual Studio, pressione **Ctrl + F5** (**Depurar** > **Iniciar sem Depuração**) para executar o aplicativo no navegador.

    O aplicativo será aberto em uma nova guia do navegador.

1. Escolha **Depurar** > **Anexar ao Processo**.

1. Na caixa de diálogo **Anexar ao Processo**, escolha **Código WebKit** no campo **Anexar a**, digite **Chrome** na caixa de filtro para filtrar o resultados da pesquisa.

1. Selecione o processo do Chrome com a porta de host correta (1337 neste exemplo) e clique em **Anexar**.

    ![Anexar ao processo](../nodejs/media/tutorial-nodejs-react-attach-to-process.png)

    Você sabe que o depurador foi anexado corretamente quando o Explorador do DOM e o Console do JavaScript são abertos no Visual Studio. Essas ferramentas de depuração são semelhantes às Ferramentas para Desenvolvedores do Chrome e às Ferramentas F12 para Edge.

    > [!NOTE]
    > Se o depurador não for anexado e a mensagem "Não é possível anexar ao processo. Uma operação não é legal no estado atual." for exibida, use o Gerenciador de Tarefas para fechar todas as instâncias do Chrome antes de iniciar o Chrome no modo de depuração. As extensões do Chrome podem estar em execução e impedindo o modo de depuração completa.

1. Como o código com o ponto de interrupção já foi executado, atualize a página do navegador para atingir o ponto de interrupção.

    Enquanto estiver em pausa no depurador, você pode examinar o estado do aplicativo passando o mouse sobre as variáveis e usando as janelas do depurador. Você pode avançar o depurador percorrendo o código (**F5**, **F10** e **F11**).

    Você pode atingir o ponto de interrupção em *app-bundle.js* ou sua localização mapeada em *app.tsx*, dependendo do estado do ambiente e do navegador. De qualquer forma, você pode percorrer o código e examinar as variáveis.

    * Se você precisar entrar no código em *app.tsx* e não conseguir, use **Anexar ao Processo**, conforme descrito nas etapas anteriores para anexar o depurador. Em seguida, abra o arquivo *app.tsx* gerado dinamicamente no Gerenciador de Soluções abrindo **Documentos de Script** > **app.tsx**, defina um ponto de interrupção e atualize a página no navegador.

        Como alternativa, se você precisar entrar no código em *app.tsx* e não conseguir, tente usar a instrução `debugger;` em *app.tsx* ou configure pontos de interrupção nas Ferramentas para Desenvolvedores do Chrome.

    * Se você precisar entrar no código em *app-bundle.js* e não conseguir, remova o arquivo sourcemap, *app-bundle.js.map*.

    > [!TIP]
    > Após anexar ao processo pela primeira vez seguindo estas etapas, você pode rapidamente anexar novamente ao mesmo processo no Visual Studio 2017 escolhendo **Depurar** > **Reanexar ao Processo**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a criar um aplicativo Node.js e React, a transcompilar JSX e a depurar. Para saber mais sobre as Ferramentas Node.js para Visual Studio, consulte a página de Wiki.

> [!div class="nextstepaction"]
> [Ferramentas Node.js para Visual Studio](https://github.com/Microsoft/nodejstools)
