---
title: Criar um aplicativo Node.js e Express – Visual Studio | Microsoft Docs
description: Neste tutorial, você cria um aplicativo Node.js e Express no Visual Studio
ms.custom: ''
ms.date: 03/13/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f7d0774753178c9cb0dbcae1800da6b00ab02a0e
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Tutorial: Criar um aplicativo Node.js e Express no Visual Studio
Neste tutorial para desenvolvimento no Visual Studio usando Node.js e Express, você criará um aplicativo Web Node.js simples, adicionará código a ele, explorará alguns recursos do IDE e executará o aplicativo. Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.  

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Criar um projeto Node.js
> * Adicionar código
> * Usar o IntelliSense
> * Executar o aplicativo
> * Atingir um ponto de interrupção

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter o Visual Studio instalado e a carga de trabalho de desenvolvimento de Node.js.

    Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo projeto**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**.

* Você precisa ter o tempo de execução do Node.js instalado.

    Se não o tiver instalado, instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/). Em geral, o Visual Studio detecta automaticamente o tempo de execução do Node.js instalado. Se ele não detectar um tempo de execução instalado, você poderá configurar seu projeto para fazer referência ao tempo de execução instalado na página de propriedades (depois de criar um projeto, clique com botão direito do mouse no nó do projeto e escolha **Propriedades**).

    Este tutorial foi testado com o Node.js 8.10.0.

## <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto de aplicativo Web Node.js.

1. Abra o Visual Studio 2017.  

1. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.  

1. Na caixa de diálogo **Novo projeto**, no painel esquerdo, expanda **JavaScript** e escolha **Node.js**. No painel central, selecione **Aplicativo Basic Azure Node.js Express 4** e, em seguida, escolha **OK**.   

     Se não vir o modelo de projeto **Aplicativo Basic Azure Node.js Express 4**, você deverá instalar a carga de trabalho de **desenvolvimento do Node.js** primeiro. 

    O Visual Studio cria a nova solução e abre seu projeto. O arquivo de projeto *app.js* é aberto no editor (painel esquerdo).

    - O seu projeto está realçado em negrito, usando o nome que você forneceu na caixa de diálogo **Novo Projeto**. No sistema de arquivos, este projeto é representado por um arquivo *.njsproj* na pasta do projeto. Você pode definir propriedades e variáveis de ambiente associadas ao projeto clicando com o botão direito do mouse no projeto e escolhendo **Propriedades**. Você pode fazer o ciclo com outras ferramentas de desenvolvimento, porque o arquivo de projeto não faz alterações personalizadas na fonte do projeto Node.js.

    - No nível superior está uma solução que, por padrão, tem o mesmo nome que o projeto. Uma solução, representada por um arquivo *.sln* no disco, é um contêiner para um ou mais projetos relacionados.

    - O nó de npm mostra os pacotes npm instalados. Você pode clicar com o botão direito do mouse no nó de npm para pesquisar e instalar pacotes de npm usando uma caixa de diálogo.

    - Arquivos de projeto como *app.js* aparecem no nó do projeto. *app.js* é o arquivo de inicialização do projeto.

1. Abra o nó **npm** e certifique-se de que todos os pacotes de npm necessários estejam presentes.

    Se algum deles estiver ausente (ícone de ponto de exclamação), clique com o botão direito do mouse no nó **npm** e escolha **Instalar Pacotes npm Ausentes**.

## <a name="add-some-code"></a>Adicionar código

1. No Gerenciador de Soluções (painel direito), abra a pasta de exibições e abra *index.pug*.

1. Substitua o conteúdo pela seguinte marcação.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. Na pasta de rotas, abra *index.js*.

1. Adicione o código a seguir antes da chamada para `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Substitua a chamada da função `router.get` pelo seguinte código:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Há um erro na linha de código que contém `res.render`. É necessário corrigi-lo antes de executar o aplicativo. Corrigiremos o erro na próxima seção.

## <a name="use-intellisense"></a>Usar o IntelliSense

1. Em *index.js*, vá para a linha de código que contém `res.render`.

1. Depois da cadeia de caracteres `data`, digite `: get` e o IntelliSense mostrará a função `getData`. Selecione `getData`.

    ![Usar o IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Remova a vírgula (`,`) antes de `"data"` e você verá o realce de sintaxe verde na expressão. Passe o mouse sobre o realce de sintaxe.

    ![Exibir erro de sintaxe](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    A última linha desta mensagem informa que o interpretador de JavaScript esperava uma vírgula (`,`).

1. Clique na guia **Lista de Erros**.

    Você verá o aviso e a descrição juntamente com o nome de arquivo e número de linha.

    ![Exibir lista de erros](../nodejs/media/tutorial-nodejs-error-list.png)

1. Corrija o código adicionando a vírgula (`,`) antes de `"data"`.

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção

1. Em *index.js*, clique na medianiz esquerda antes da seguinte linha de código para definir um ponto de interrupção:

    `res.render('index', { title: 'Express', "data": getData() });`

    Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não. 

    ![Definir um ponto de interrupção](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Executar o aplicativo

1. Selecione o destino de depuração na barra de ferramentas Depurar.

    ![Selecionar o destino de depuração](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Pressione **F5** (**Depurar** > **Iniciar Depuração**) para executar o aplicativo.

    O depurador faz uma pausa no ponto de interrupção que você definir. Agora, você pode inspecionar o estado do aplicativo.

1. Passe o mouse sobre `getData` para ver suas propriedades em um DataTip

    ![Inspecionar variáveis](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Pressione **F5** (**Depurar** > **Continuar**) para continuar.

    O aplicativo é aberto em um navegador.

    Na janela do navegador, você verá “Express” como o título e “Bem-vindo ao Express” no primeiro parágrafo.

1. Clique nos botões para exibir diferentes imagens.

    ![Aplicativo em execução no navegador](../nodejs/media/tutorial-nodejs-running-in-browser.png)  

1. Feche o navegador da Web.  

## <a name="optional-publish-to-azure-app-service"></a>(Opcional) Publicar no Serviço de Aplicativo do Azure

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**.

   ![Publicar no Serviço de Aplicativo do Azure](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. Escolha **Serviço de Aplicativo do Microsoft Azure**.

    Na caixa de diálogo **Serviço de Aplicativo**, você pode entrar na sua conta do Azure e conectar-se a assinaturas do Azure existentes.

1. Siga as etapas restantes para selecionar uma assinatura, escolha ou crie um grupo de recursos, escolha ou crie um plano de serviço de aplicativo e, em seguida, siga as etapas quando solicitado para publicar no Azure. Para obter instruções mais detalhadas, consulte [Publicar no site do Azure usando a implantação da Web](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. A janela **Saída** mostra o andamento na implantação para o Azure.

    Em uma implantação bem-sucedida, o aplicativo é aberto em um navegador em execução no serviço de aplicativo do Azure. Clique em um botão para exibir uma imagem.

   ![Aplicativo em execução no Serviço de Aplicativo do Azure](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

Parabéns por concluir este tutorial.

## <a name="next-steps"></a>Próximas etapas 

Neste tutorial, você aprendeu a criar e executar um aplicativo Node.js usando Express e a atingir um ponto de interrupção usando o depurador.

> [!div class="nextstepaction"]
> [Ferramentas Node.js para Visual Studio](https://github.com/Microsoft/nodejstools)