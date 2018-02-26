---
title: "Introdução ao Node.js no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1d91d46b20f82a1700c2d20639b3a8827c92bcb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Introdução ao Node.js no Visual Studio
Neste tutorial para desenvolvimento em Node.js usando o Visual Studio, você criará um aplicativo Web Node.js, adicionará código a ele, explorará alguns recursos do IDE e executará o aplicativo. Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.  

## <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto de aplicativo Web Node.js.

1. Abra o Visual Studio 2017.  

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.  

3. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **JavaScript** e escolha **Node.js**. No painel central, escolha **Aplicativo Basic Azure Node.js Express 4** e, em seguida, escolha **OK**.   

     Se você não vir o modelo de projeto do **Aplicativo Basic Azure Node.js Express 4**, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**. 

    O Visual Studio cria a nova solução e abre seu projeto. O arquivo de projeto **app.js** é aberto no editor (painel esquerdo). Se você não estiver familiarizado com projetos e soluções do Visual Studio, consulte [Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Node.js](../ide/quickstart-nodejs.md).

4. Se você não tiver o tempo de execução do Node.js já instalado, instale-o do site do [Node.js](https://nodejs.org/en/download/).

    Em geral, o Visual Studio detecta automaticamente o tempo de execução do Node.js instalado. Se ele não detectar um tempo de execução instalado, você poderá configurar seu projeto para referenciar o tempo de execução instalado.

## <a name="add-some-code"></a>Adicionar código

1. No Gerenciador de Soluções (painel direito), abra a pasta de exibições e abra index.pug.

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

1. Na pasta de rotas, abra index.js.

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

1. Depois de `data`, digite `: get` e o IntelliSense mostrará a função getData. Selecione `getData`.

    ![Usar o IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Remova a vírgula (`,`) antes de `"data"` e você verá o realce de sintaxe verde na expressão. Passe o mouse sobre o realce de sintaxe.

    ![Exibir erro de sintaxe](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    A última linha desta mensagem informa que o interpretador de JavaScript esperava uma vírgula (`,`).

1. Clique na guia **Lista de Erros**.

    Você verá o aviso e a descrição juntamente com o nome de arquivo e número de linha.

    ![Exibir lista de erros](../nodejs/media/tutorial-nodejs-error-list.png)

1. Corrija o código adicionando a vírgula (`,`) antes de `"data"`.

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção

1. Em index.js, clique na medianiz esquerda antes da seguinte linha de código para definir um ponto de interrupção:

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

1. Abra a Janela Interativa Node.js selecionando **Exibir** > **Outras Janelas** > **Janela Interativa Node.js**.

   ![Abrir a Janela Interativa do Node.js](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    A janela interativa é compatível com tudo o que você pode fazer no código, incluindo o uso de instruções `require()`. O código na captura de tela a seguir define uma variável e exibe o local do intérprete do Node.js.

   ![Janela Interativa do Node.js](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

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

- Saiba mais sobre as [Ferramentas Node.js para Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- Saiba mais sobre o [IDE do Visual Studio](../ide/visual-studio-ide.md)  