---
title: "Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Node.js | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.workload: nodejs
ms.openlocfilehash: 12c848797b167038b02106ca3392cac50171f699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Node.js
Nesta introdução de 5 a 10 minutos do IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo Web Node.js simples. Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.  

## <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto de aplicativo Web Node.js.

1. Abra o Visual Studio 2017.  

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.  

3. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **JavaScript** e escolha **Node.js**. No painel central, escolha **Aplicativo Web Node.js em branco** e, em seguida, escolha **OK**.   

     Se você não vir o modelo de projeto do **Aplicativo Web Node.js em branco**, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**.  

     ![Carga de trabalho Node.js no instalador do VS](../ide/media/quickstart-nodejs-workload.png)  

    O Visual Studio cria a nova solução e abre o projeto. **Server.js** aberto no editor.

## <a name="explore-the-ide"></a>Explorar o IDE  

1. Observe o **Gerenciador de Soluções** no painel direito.

   ![Gerenciador de Soluções](../ide/media/quickstart-nodejs-solution-explorer.png)  

  - O seu projeto está realçado em negrito, usando o nome que você forneceu na caixa de diálogo **Novo Projeto**. No disco, este projeto é representado por um arquivo .njproj na pasta do projeto.

  - No nível superior está uma solução que, por padrão, tem o mesmo nome que o projeto. Uma solução, representada por um arquivo .sln no disco, é um contêiner para um ou mais projetos relacionados.

  - O nó de npm mostra os pacotes npm instalados. Você pode clicar com o botão direito do mouse no nó de npm para pesquisar e instalar pacotes de npm usando uma caixa de diálogo.

1. Se você deseja instalar pacotes de npm ou comandos do Node.js de um prompt de comando, clique com botão direito do mouse no nó do projeto e escolha **Abrir prompt de comando aqui**.

   ![Prompt de comando do Node.js](../ide/media/quickstart-nodejs-command-prompt.png) 

1. No arquivo **server.js** no editor (painel esquerdo), escolha `http.createServer` e pressione **F12** ou escolha **Ir para Definição** no menu de contexto (acessado com o clique do botão direito do mouse). Esse comando acessará a definição da função `createServer` em index.d.ts.  

   ![Menu de contexto de Ir para Definição](../ide/media/quickstart-nodejs-gotodefinition.png)  

1. Coloque o cursor no final da cadeia de caracteres nesta linha de código, `res.end('Hello World\n');`, e modifique-o para que fique assim:

    `res.end('Hello World\n' + res.connection.`

    Quando você digita `connection.`, o IntelliSense fornece opções para completar automaticamente a entrada de código.

   ![Preenchimento automático do IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)  

1. Escolha **localPort**e, em seguida, digite `);` para completar a instrução para que ela fique assim:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Executar o aplicativo
1. Pressione **Ctrl+F5** (ou **Depurar > Iniciar Sem Depuração**) para executar o aplicativo. O aplicativo é aberto em um navegador.  

1. Na janela do navegador, você verá “Olá, Mundo”, além do número da porta local.

1. Feche o navegador da Web.  

Parabéns por concluir este guia de início rápido! Esperamos que você tenha aprendido um pouco sobre o IDE do Visual Studio. Se você quiser se aprofundar mais em seus recursos, continue com um tutorial na seção **Tutoriais** do sumário.  

## <a name="next-steps"></a>Próximas etapas 

- Passar pelo [Tutorial para Node.js](../nodejs/tutorial-nodejs.md)  
- Saiba mais sobre o [IDE do Visual Studio](../ide/visual-studio-ide.md)  
- Saiba mais sobre as [Ferramentas Node.js para Visual Studio](https://github.com/Microsoft/nodejstools/wiki)