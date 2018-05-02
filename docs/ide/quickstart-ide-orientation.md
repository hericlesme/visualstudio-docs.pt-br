---
title: Tour do IDE do Visual Studio
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd72de016e9f44987fae43e7b49820e21af0a288
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Início rápido: Introdução ao IDE do Visual Studio

Nesta introdução de 5 a 10 minutos ao IDE (Ambiente de Desenvolvimento Integrado) do Visual Studio, faremos um tour em algumas janelas, menus e em outros recursos de interface do usuário.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="start-page"></a>Start Page

A primeira coisa que você verá depois de iniciar o Visual Studio provavelmente será a **Página Inicial**. A **Página Inicial** foi projetada como um "hub" para ajudá-lo a localizar os comandos e os arquivos de projeto necessários com mais rapidez. A seção **Recentes** exibe projetos e pastas em que você trabalhou recentemente. Em **Novo projeto**, você pode clicar em um link para abrir a caixa de diálogo **Novo Projeto** ou, em **Abrir**, você pode abrir um projeto existente ou a pasta de código. À direita está um feed das notícias mais recentes do desenvolvedor.

![Página Inicial do VS](media/quickstart-IDE-start-page.png)

Se você fechar a **Página Inicial** e desejar vê-la novamente, será possível reabri-la no menu **Arquivo**.

![Menu Arquivo](media/quickstart-IDE-file-menu-large.png)

Para continuar explorando o IDE, vamos criar um novo projeto.

1. Na **Página Inicial**, na caixa de pesquisa em **Novo projeto**, insira `console` para filtrar a lista de tipos de projeto. Escolha um C# ou VB **Aplicativo do Console (.NET Framework)**. (Como alternativa, se você for um desenvolvedor de C++, Javascript ou outra linguagem, fique à vontade para criar um projeto em uma dessas linguagens. A interface do usuário que você verá é semelhante para todas as linguagens.)

1. Na caixa de diálogo **Novo Projeto**, aceite o nome padrão do projeto e escolha **OK**.

   O projeto é criado e um arquivo chamado *Program.cs* ou *Program.vb* é aberto na janela **Editor**. O **Editor** mostra o conteúdo dos arquivos e é onde você fará a maior parte do trabalho de codificação no Visual Studio.

## <a name="solution-explorer"></a>Gerenciador de Soluções

O **Gerenciador de Soluções** mostra uma representação gráfica da hierarquia de arquivos e pastas do projeto, da solução ou da pasta de código. Você pode procurar na hierarquia e navegar até algum arquivo no **Gerenciador de Soluções**.

![Gerenciador de Soluções](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menus

A barra de menus na parte superior do IDE agrupa comandos em categorias. Por exemplo, o menu **Projeto** contém comandos relacionados ao projeto em que você está trabalhando. No menu **Ferramentas**, você pode personalizar o IDE selecionando **Opções** ou adicionar recursos na sua instalação selecionando **Obter Ferramentas e Recursos**.

![Barra de menus](media/quickstart-IDE-menu-bar.png)

Vamos abrir a janela **Lista de Erros** escolhendo o menu **Exibir** e, em seguida, **Lista de Erros**.

## <a name="error-list"></a>Lista de Erros

A **Lista de Erros** mostra erros, avisos e mensagens sobre o estado atual do código. Se houver erros (como um erro de digitação de sintaxe) em seu arquivo ou em qualquer lugar no seu projeto, eles estarão listados aqui.

![Lista de Erros](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>janela Saída

A janela **Saída** mostra as mensagens de saída do build e do controle do código-fonte.

Vamos criar o projeto para ver alguns logs de saída. No menu **Compilação**, escolha **Compilar Solução**. A janela **Saída** obtém o foco automaticamente e exibe uma mensagem de build bem-sucedido.

![Janela Saída](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Início Rápido

A caixa **Início Rápido** é uma maneira rápida e fácil de fazer praticamente tudo no IDE. Você pode inserir um texto relacionado ao que você deseja fazer e ele mostrará uma lista de opções que pertencem ao texto. Por exemplo, digamos que você queira aumentar o detalhamento da saída da compilação para exibir mais informações de log sobre o que exatamente a compilação está fazendo:

1. Insira `verbosity` na caixa **Início Rápido** e escolha **Projetos e Soluções -> Compilar e Executar** na categoria **Opções**.

   ![Caixa Início Rápido](media/quickstart-IDE-quick-launch.png)

   A caixa de diálogo **Opções**é aberta na página de opções **Compilar e Executar**.

1. Em **Detalhes da saída de build do projeto do MSBuild**, escolha **Normal** e clique em **OK**.

1. Agora, criaremos o projeto novamente clicando com o botão direito do mouse no projeto **ConsoleApp1** no **Gerenciador de Soluções** e escolhendo **Recriar** no menu de contexto.

   Desta vez, a janela **Saída** mostra o log detalhado do processo de build, incluindo quais arquivos foram copiados e onde.

## <a name="send-feedback-menu"></a>Menu Enviar Comentários

Se você encontrar problemas enquanto estiver usando o Visual Studio ou se tiver sugestões de como melhorar o produto, use o menu **Enviar Comentários** na parte superior do IDE, ao lado da caixa **Início Rápido**.

![Menu Enviar Comentários](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Próximas etapas

Vimos apenas alguns dos recursos do IDE do Visual Studio para nos familiarizarmos com a interface do usuário. Para explorar mais:

- Procure a seção **Elementos Gerais de Interface do Usuário** da documentação do VS, que dá mais detalhes sobre janelas como [Lista de Erros](../ide/reference/error-list-window.md), [Saída](../ide/reference/output-window.md), [Propriedades](../ide/reference/properties-window.md) e [Caixa de diálogo de Opções](../ide/reference/options-dialog-box-visual-studio.md)

- Faça um tour mais detalhado pelo IDE e até mesmo explore a depuração na [Visão geral do IDE do Visual Studio](../ide/visual-studio-ide.md)

## <a name="see-also"></a>Consulte também

- [Início rápido: personalizar o IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Início rápido: Codificação no editor](../ide/quickstart-editor.md)
- [Início rápido: projetos e soluções](../ide/quickstart-projects-solutions.md)