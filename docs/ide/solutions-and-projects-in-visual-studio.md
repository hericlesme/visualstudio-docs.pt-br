---
title: Soluções e projetos no Visual Studio
ms.date: 10/5/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6be610e60c35ef22306398f56375bfa6185e1e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluções e projetos no Visual Studio

## <a name="projects"></a>Projetos

Ao criar um aplicativo, um site, um plug-in, etc. no Visual Studio, você inicia um *projeto*. Logicamente, um projeto contém todos os arquivos de código-fonte, ícones, imagens, arquivos de dados, etc. que são compilados em um executável, biblioteca ou site. Um projeto também contém as configurações de compilador e outros arquivos de configuração que podem ser necessários para diversos serviços ou componentes com os quais seu programa se comunica.

> [!NOTE]
> Você não precisa usar soluções ou projetos no Visual Studio para editar, compilar e depurar o código. Você pode simplesmente abrir a pasta que contém os arquivos de origem no Visual Studio e começar a editá-los. Para obter mais informações, consulte [Desenvolver código no Visual Studio sem projetos nem soluções](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Um projeto é definido em um arquivo XML com uma extensão, como *.vbproj*, *.csproj* ou *.vcxproj*. Este arquivo contém uma hierarquia de pasta virtual e os caminhos para todos os itens no projeto. Ele também contém as configurações de build.

> [!TIP]
> Para examinar o conteúdo de um arquivo de projeto no Visual Studio, primeiro descarregue o projeto selecionando o nome do projeto no **Gerenciador de Soluções** e escolhendo **Descarregar Projeto** no menu de contexto ou de clique com o botão direito do mouse. Em seguida, abra o menu de contexto novamente e escolha **Editar \<projectname\>**.

No Visual Studio, o arquivo de projeto é usado pelo **Gerenciador de Soluções** para exibir as configurações e o conteúdo do projeto. Quando você compila seu projeto, o mecanismo do MSBuild consome o arquivo de projeto para criar o executável. Você também pode personalizar os projetos para produzir outros tipos de saída.

## <a name="solutions"></a>Soluções

Um projeto está contido dentro de uma *solução*. Uma solução contém um ou mais projetos relacionados, juntamente com informações de build, configurações de janela do Visual Studio e arquivos diversos que não estão associados a nenhum projeto específico. Uma solução é descrita por um arquivo de texto (extensão *.sln*) com seu próprio formato exclusivo, que não se destina à edição manual.

Uma solução tem um arquivo *.suo* associado que armazena as configurações, as preferências e as informações de configuração de cada usuário que trabalhou no projeto.

## <a name="create-new-projects"></a>Criar novos projetos

A maneira mais fácil de criar um novo projeto é começar de um modelo de projeto para um tipo específico de aplicativo ou site. Um modelo de projeto consiste em um conjunto básico de arquivos de código, arquivos de configuração, ativos e configurações gerados previamente. Esses modelos são o que você vê na caixa de diálogo **Novo Projeto** ou **Novo Site** quando escolhe **Arquivo** > **Novo** > **Projeto** ou **Arquivo** > **Novo** > **Site**. Para obter mais informações, confira [Criar soluções e projetos](../ide/creating-solutions-and-projects.md).

Também é possível criar modelos de item e de projeto personalizados. Para obter mais informações, confira [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Gerenciar projetos no Gerenciador de Soluções

Depois de criar um novo projeto, você pode usar o **Gerenciador de Soluções** para exibir e gerenciar o projeto, a solução e seus itens associados. A ilustração a seguir mostra o **Gerenciador de Soluções** com uma solução em C# que contém dois projetos.

![Gerenciador de Soluções](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")

## <a name="see-also"></a>Consulte também

- [Visual Studio IDE](../ide/visual-studio-ide.md)