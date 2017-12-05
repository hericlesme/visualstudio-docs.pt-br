---
title: "Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Web ASP.NET Core | Microsoft Docs"
ms.custom: 
ms.date: 10/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: e87c46d1d78fafdc629a9f08e0bd7afacc1e1f3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Início rápido: usar o Visual Studio para criar seu primeiro aplicativo Web ASP.NET Core
Nesta introdução de 5 a 10 minutos do IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo Web simples ASP.NET Core em C#. Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.  

## <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto de aplicativo Web ASP.NET Core. O tipo de projeto vem com arquivos de modelo que constituem um aplicativo Web funcional, mesmo sem adicionar nada!  

1. Abra o Visual Studio 2017.  

1. Na barra de menus superior, escolha **Arquivo**, **Novo**, **Projeto...**.  

1. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda **Visual C#** e, em seguida, escolha **.NET Core**. No painel central, escolha **Aplicativo Web ASP.NET Core** e, em seguida, selecione **OK**.   

     Se o modelo de projeto **.NET Core** não for exibido, cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas**, **Obter Ferramentas e Recursos...**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.  

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

1. Serão exibidos dois sublinhados ondulados sob **Ambiente** e **Cadeia de caracteres**, porque esses tipos não estão no escopo. Abra a barra de ferramentas **Lista de Erros** para ver os mesmos erros listados. (Se a barra de ferramentas **Lista de Erros** não for exibida, escolha **Exibir**, **Lista de Erros** na barra de menus superior.)  

   ![Lista de Erros](../ide/media/quickstart-aspnet-errorlist.png)  

1. Na janela do editor, coloque o cursor em um linha que contenha o erro e, em seguida, escolha a lâmpada Ações Rápidas na margem esquerda. No menu suspenso, escolha **using System;** para adicionar essa diretiva no topo do arquivo e resolver os erros.  

## <a name="run-the-application"></a>Executar o aplicativo
1. Pressione **Ctrl + F5** para executar o aplicativo e abri-lo em um navegador da Web.  

1. Na parte superior do site, escolha **Sobre** para ver o diretório de mensagem que você adicionou no método `OnGet()` da página **Sobre**.  

1. Feche o navegador da Web.  

Parabéns por concluir este guia de início rápido! Esperamos que você tenha aprendido um pouco sobre o IDE do Visual Studio. Se você quiser se aprofundar mais em seus recursos, continue com um tutorial na seção **Tutoriais** do sumário.  

## <a name="see-also"></a>Consulte também   
[Introdução ao C# e ao Visual Basic usando o Visual Studio](getting-started-with-visual-csharp-and-visual-basic.md)
[Introdução a páginas Razor no ASP.NET Core](/aspnet/core/tutorials/razor-pages/razor-pages-start)  