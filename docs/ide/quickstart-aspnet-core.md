---
title: Usar o Visual Studio para criar um aplicativo Web ASP.NET Core em C#
description: Saiba como criar um aplicativo Web do ASP.NET Core no Visual Studio com C#, passo a passo.
ms.custom: mvc
ms.date: 10/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: e030a3e3870746cda7ae98f5c4b45d29c8ba4885
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Início rápido: Usar o Visual Studio para criar seu primeiro aplicativo Web ASP.NET Core

Nesta introdução de 5 a 10 minutos do IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo Web simples ASP.NET Core em C#.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto de aplicativo Web ASP.NET Core. O tipo de projeto vem com arquivos de modelo que constituem um aplicativo Web funcional, mesmo sem adicionar nada!

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **Visual C#** e, em seguida, escolha **.NET Core**. No painel central, escolha **Aplicativo Web ASP.NET Core** e, em seguida, selecione **OK**.

     Se você não vir a categoria de modelo de projeto **.NET Core**, escolha o link **Abrir Instalador do Visual Studio** no painel esquerdo. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

     ![Carga de trabalho ASP.NET no instalador do VS](../ide/media/quickstart-aspnet-workload.png)

1. Na caixa de diálogo **Novo aplicativo Web ASP.NET Core**, selecione **ASP.NET Core 2.0** no menu suspenso superior. (Se o **ASP.NET Core 2.0** não aparecer na lista, instale-o seguindo o link **Baixar** que deve aparecer em uma barra amarela próxima à parte superior da caixa de diálogo.) Escolha **OK**.

   ![Caixa de diálogo Novo Aplicativo Web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Explorar o IDE

1. Na barra de ferramentas **Gerenciador de Soluções**, expanda a pasta **Páginas** e, em seguida, escolha **About.cshtml** para abri-lo no editor. Este arquivo corresponde a uma página chamada **Sobre** no aplicativo Web.

1. No editor, escolha `AboutModel` e, em seguida, pressione **F12** ou escolha **Ir para Definição** no menu de contexto (acessado com o clique do botão direito do mouse). Esse comando acessará a definição da classe C# `AboutModel`.

   ![Menu de contexto de Ir para Definição](../ide/media/quickstart-aspnet-gotodefinition.png)

1. Em seguida você removerá as diretivas `using` no topo do arquivo usando um atalho simples. Escolha uma das diretivas using esmaecidas e será exibida uma lâmpada [Ações Rápidas](../ide/quick-actions.md) logo abaixo da seta ou na margem esquerda. Escolha a lâmpada e, em seguida, escolha **Remover Usings Desnecessários**.

     Os usings desnecessários serão excluídos do arquivo.

1. No método `OnGet()`, altere o corpo para o código a seguir:

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Serão exibidos dois sublinhados ondulados sob **Ambiente** e **Cadeia de caracteres**, porque esses tipos não estão no escopo. Abra a barra de ferramentas **Lista de Erros** para ver os mesmos erros listados. (Se a barra de ferramentas **Lista de Erros** não for exibida, escolha **Exibir** > **Lista de Erros** na barra de menus superior.)

   ![Lista de Erros](../ide/media/quickstart-aspnet-errorlist.png)

1. Na janela do editor, coloque o cursor em uma linha que contenha o erro e, em seguida, escolha a **lâmpada Ações Rápidas** na margem esquerda. No menu suspenso, escolha **using System;** para adicionar essa diretiva no topo do arquivo e resolver os erros.

## <a name="run-the-application"></a>Executar o aplicativo

1. Pressione **Ctrl**+**F5** para executar o aplicativo e abri-lo em um navegador da Web.

1. Na parte superior do site, escolha **Sobre** para ver o diretório de mensagem que você adicionou no método `OnGet()` da página **Sobre**.

1. Feche o navegador da Web.

> [!NOTE]
> Se você receber uma mensagem de erro que diz **Não é possível se conectar ao servidor Web ‘IIS Express’**, feche o Visual Studio e, então, abra-o usando a opção **Executar como administrador** ao clicar com o botão direito do mouse ou no menu de contexto. Em seguida, execute o aplicativo novamente.

Parabéns por concluir este Guia de Início Rápido! Esperamos que você tenha aprendido um pouco sobre o IDE do Visual Studio. Se você quiser se aprofundar mais em seus recursos, continue com um tutorial na seção **Tutoriais** do sumário.

## <a name="next-steps"></a>Próximas etapas
Parabéns por concluir este Guia de Início Rápido! Esperamos que você tenha aprendido um pouco sobre o C#, o ASP.NET Core e o IDE do Visual Studio. Para saber mais, continue com o tutorial a seguir.

> [!div class="nextstepaction"]
> [Introdução ao C# e ao ASP.NET no Visual Studio](tutorial-csharp-aspnet-core.md)
