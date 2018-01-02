---
title: "Introdução à linguagem C++ no Visual Studio | Microsoft Docs"
ms.custom: mvc
ms.date: 12/04/2017
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
author: corob-msft
ms.author: tglee
manager: ghogen
ms.openlocfilehash: c86e7bcfe43eeaa6554efeed6654f34e140d9ea7
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2017
---
# <a name="get-started-with-c-in-visual-studio"></a>Introdução à linguagem C++ no Visual Studio

Complete este guia de início rápido para se familiarizar com várias ferramentas e caixas de diálogo que poderá usar ao desenvolver aplicativos em C++ com o Visual Studio. Crie um aplicativo de console no estilo “Olá, Mundo” enquanto aprende mais sobre o trabalho no IDE (ambiente de desenvolvimento integrado).

## <a name="prerequisites"></a>Pré-requisitos

Você não precisa estar familiarizado com C++ para concluir este guia de início rápido, mas precisa conhecer um pouco de programação geral e de conceitos de depuração. A documentação do Visual Studio não ensina como programar em C++. Um bom guia para os recursos de aprendizagem de C++ é a página [Introdução](https://isocpp.org/get-started) no site de C++ da ISO.

Para acompanhar, você precisará de uma cópia do Visual Studio 2017 versão 15.3 ou posterior, com a carga de trabalho **Desenvolvimento para a área de trabalho com C++** instalada. Para obter um guia rápido de instalação, consulte [Install C++ support in Visual Studio](/cpp/build/vscpp-step-0-installation) (Suporte para a instalação de C++ no Visual Studio).

## <a name="create-a-console-app"></a>Criar um aplicativo do console

Se ele não ainda estiver em execução, inicie o Visual Studio.

![IDE com Visual C&#43;&#43; configurações aplicadas](../ide/media/get-started-cpp-ide-layout.png "IDE com Visual C&#43;&#43; configurações aplicadas")

Depois de abrir o Visual Studio, você poderá ver as três partes básicas do IDE: janelas de ferramenta, menus e barras de ferramentas e o espaço da janela principal. As janelas de ferramentas são encaixadas à esquerda e à direita da janela do aplicativo. A caixa **Início Rápido**, a barra de menus e a barra de ferramentas padrão estão na parte superior. O centro da janela contém a **Página Inicial**. Quando você abre uma solução ou um projeto, editores e designers aparecem neste espaço. Ao desenvolver um aplicativo, você passará a maior parte do seu tempo nesta área central.

O Visual Studio usa os *projetos* para organizar o código em um aplicativo e as *soluções* para organizar seus projetos. Um projeto contém todas as opções, configurações e regras usadas para criar seus aplicativos. Ele também gerencia a relação entre todos os arquivos de projeto e todos os arquivos externos. Para criar seu aplicativo, primeiro, crie um novo projeto e uma nova solução.

### <a name="to-create-a-console-app-project"></a>Para criar um projeto de aplicativo do console

1. Na barra de menus, selecione **Arquivo > Novo > Projeto** para abrir a caixa de diálogo **Novo Projeto**.

   ![Na barra de menus, selecione Arquivo > Novo > Projeto](../ide/media/get-started-cpp-file-new-project-menu.png "Na barra de menus, selecione Arquivo > Novo > Projeto")

1. Na caixa de diálogo **Novo Projeto**, selecione **Instalado > Visual C++** se ainda não estiver selecionado. No painel central, selecione o modelo **Aplicativo do Console do Windows**. Na caixa de edição **Nome**, digite *HelloApp*.

   ![Use a caixa de diálogo Novo Projeto para criar seu projeto de aplicativo](../ide/media/get-started-cpp-new-project-dialog.png "Use a caixa de diálogo Novo Projeto para criar seu projeto de aplicativo")

   A caixa de diálogo pode ter opções diferentes, dependendo das cargas de trabalho do Visual Studio e dos componentes que você instalou. Se você não vir os modelos de projeto do Visual C++, execute o Instalador do Visual Studio novamente e instale a carga de trabalho **Desenvolvimento para a área de trabalho com C++**. Você pode fazer isso diretamente da caixa de diálogo **Novo Projeto**. Para iniciar o instalador, escolha o link **Abrir Instalador do Visual Studio** na caixa de diálogo.

1. Escolha o botão **OK** para criar sua solução e projeto de aplicativo.

   O projeto e a solução HelloApp, com os arquivos básicos para um aplicativo de console Windows, são criados e automaticamente carregados no **Gerenciador de Soluções**. O arquivo HelloApp.cpp é aberto no editor de códigos. Estes itens aparecem no **Gerenciador de Soluções**:

   ![Arquivos da solução no Gerenciador de Soluções](../ide/media/get-started-cpp-solution-explorer.png "Arquivos da solução no Gerenciador de Soluções")

## <a name="add-code-to-the-app"></a>Adicionar código ao aplicativo

Em seguida, adicione o código para exibir a palavra “Hello” na janela do console.

### <a name="to-edit-code-in-the-editor"></a>Para editar o código no editor

1. No arquivo HelloApp.cpp, insira uma linha em branco antes da linha `return 0;` e, em seguida, digite este código:

   ```cpp
   cout << "Hello\n";
   ```

   Uma pequena linha vermelha aparecerá em `cout`. Se você passar o ponteiro sobre ele, uma mensagem de erro será exibida.

   ![Texto de erro para cout](../ide/media/get-started-cpp-intellisense-error.png "Texto de erro para cout")

   A mensagem de erro também aparece na janela **Lista de Erros**. Você pode exibir a janela ao selecionar **Exibir > Lista de Erros** na barra de menus.

   ![Erro na janela Lista de Erros](../ide/media/get-started-cpp-error-list.png "Erro na janela Lista de Erros")

   Uma declaração está ausente em seu código para [std::cout](/cpp/standard-library/iostream), que está em \<iostream > arquivo de cabeçalho.

1. Para incluir o cabeçalho iostream, digite este código após `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Você deve ter notado que uma caixa aparece conforme insere o código. Essa caixa contém sugestões de preenchimento automático para os caracteres que você inserir. Ela é parte do IntelliSense do C++, que fornece prompts de codificação, incluindo a classe ou os membros da interface e as informações de parâmetro. Você também pode usar trechos de código, que são blocos de código predefinidos. Para obter mais informações, consulte [Usando IntelliSense](../ide/using-intellisense.md) e [Trechos de código](../ide/code-snippets.md).

   ![O código fixo no editor](../ide/media/get-started-cpp-cout-fix.png "O código fixo no editor")

   A pequena linha vermelha em `cout` desaparecerá quando você corrigir o erro.

1. Para salvar as alterações no arquivo, pressione **Ctrl+S**.

## <a name="build-the-app"></a>Compilar o aplicativo

É fácil compilar seu código. Na barra de menus, escolha **Compilar > Compilar Solução**. O Visual Studio compila a solução HelloApp e relata o progresso na Janela de **Saída**.

   ![Compilar a solução HelloApp](../ide/media/get-started-cpp-build-solution.gif "Compilar a solução HelloApp")

## <a name="debug-and-test-the-app"></a>Depurar e testar o aplicativo

Você pode depurar o HelloApp para ver se a palavra “Hello” aparece na janela do console.

### <a name="to-debug-the-app"></a>Para depurar o aplicativo

1. Para iniciar o depurador, escolha **Depurar > Iniciar Depuração** na barra de menus.

   ![Iniciar o comando de depuração no menu Depurar](../ide/media/get-started-cpp-start-debugging-menu.png "Iniciar o comando de depuração no menu Depurar")

   O depurador inicia e executa o código. A janela de console (uma janela separada que se parece com um prompt de comando) é exibida por alguns segundos mas fecha rapidamente quando o depurador interrompe a execução. Para ver o texto, você precisa definir um ponto de interrupção para interromper a execução do programa.

### <a name="to-add-a-breakpoint"></a>Para adicionar um ponto de interrupção

1. No editor, coloque o cursor na linha `return 0;`. Na barra de menus, escolha **Depurar > Alternar Ponto de Interrupção**. Você também pode clicar na margem esquerda para definir um ponto de interrupção.

     ![Alternar o comando de ponto de interrupção no menu Depurar](../ide/media/get-started-cpp-toggle-breakpoint-menu.png "Alternar o comando de ponto de interrupção no menu Depurar")

     Um círculo vermelho aparece ao lado da linha de código na margem da extrema esquerda da janela do editor.

     ![Ponto de interrupção indicado na margem da janela](../ide/media/get-started-cpp-breakpoint-set.png "Ponto de interrupção indicado na margem da janela")

1. Para iniciar a depuração, pressione **F5**.

   O depurador é iniciado e uma janela de console aparece mostrando a palavra **Hello**.

   ![Texto Olá na janela do console](../ide/media/get-started-cpp-helloapp-window.png "Texto Olá na janela do console")

1. Para interromper a depuração, pressione **Shift + F5**.

Para obter mais informações sobre a depuração de projeto do console, consulte [Projetos de Console](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Criar uma versão de lançamento do app

Agora que você verificou que tudo está funcionando, já pode preparar um build de versão do aplicativo. Os builds da versão deixam de lado as informações de depuração e usam as opções de otimização do compilador para criar um código menor e mais rápido.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Para limpar os arquivos de solução e criar uma versão de lançamento

1. Na barra de menus, escolha **Build > Limpar solução** para excluir arquivos intermediários e arquivos de saída criados durante builds anteriores.

   ![O comando Limpar Solução no menu Compilar](../ide/media/get-started-cpp-clean-solution-menu.png "ExploreIDE-CleanSolution")

1. Para alterar a configuração da solução para HelloApp de **Depurar** para **Versão**, na barra de ferramentas, selecione o menu suspenso no controle Configurações de Solução e escolha **Versão**.

   ![Criar uma versão de lançamento do aplicativo](../ide/media/get-started-cpp-set-release-configuration.png "C++IDE_ChangingBuildtoRelease")

1. Compile a solução. Na barra de menus, escolha **Compilar > Compilar Solução**.

Quando este build for concluído, você terá criado um aplicativo que poderá copiar e ser executado em qualquer janela de prompt de comando. Ele pode não fazer muito, mas é o gateway para coisas maiores.

Parabéns por concluir este guia de início rápido! Se desejar explorar mais exemplos, consulte [Amostras do Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Consulte também

[Usando o IDE do Visual Studio para desenvolvimento de área de trabalho do C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)  
[Passo a passo: criar um aplicativo simples com o Visual C# ou o Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)  
[Dicas de produtividade para o Visual Studio](../ide/productivity-tips-for-visual-studio.md)  
[Exemplos do Visual Studio](../ide/visual-studio-samples.md)  
[Introdução ao desenvolvimento com o Visual Studio](../ide/get-started-developing-with-visual-studio.md)
