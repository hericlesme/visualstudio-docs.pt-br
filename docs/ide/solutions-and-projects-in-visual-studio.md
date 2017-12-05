---
title: "Soluções e projetos no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluções e projetos no Visual Studio
Ao criar um aplicativo, um site, um plug-in, etc. no Visual Studio, você inicia um *projeto*. Em um sentido lógico, um projeto contém de todos os arquivos de código-fonte, ícones, imagens, arquivos de dados e qualquer outra coisa que será compilada em um programa executável ou site, ou o que mais for necessário para executar a compilação. Um projeto também contém todas as configurações de compilador e outros arquivos de configuração que podem ser necessários para diversos serviços ou componentes com os quais seu programa se comunicará.  

> [!NOTE]
>  Você não será obrigado a usar soluções ou projetos se não desejar. Você pode simplesmente abrir os arquivos no Visual Studio e começar a editar seu código. Consulte [Desenvolver código no Visual Studio sem projetos nem soluções](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) para obter mais informações.  

Um arquivo de projeto (.vbproj, .csproj, .vcxproj) é um arquivo XML que define uma hierarquia de pastas virtuais junto com os caminhos para todos os itens no projeto. Ele também contém as configurações de build. Para ver o conteúdo de um arquivo de projeto, você pode selecionar o nome do projeto no Gerenciador de Soluções e escolher **Descarregar projeto** no menu de contexto (acessado com o clique do botão direito do mouse). Em seguida, abra o menu de contexto novamente e escolha **Editar \<projectname\>**.  

No Visual Studio, o arquivo de projeto é usado pelo Gerenciador de Soluções para exibir as configurações e o conteúdo do projeto. Quando você compila seu projeto, o mecanismo do MSBuild consome o arquivo de projeto para criar o executável. Você também pode personalizar os projetos para produzir outros tipos de saída.  

Em um sentido lógico e no sistema de arquivos, um projeto está contido em uma *solução*, que pode conter um ou mais projetos relacionados, juntamente com informações de build, configurações de janela do Visual Studio e arquivos diversos que não estão associados a nenhum projeto específico. Uma solução é descrita por um arquivo de texto (.sln) com seu próprio formato exclusivo, que geralmente não se destina à edição manual.  

Uma solução tem um arquivo *.suo* associado que armazena as configurações, preferências e informações de configuração de cada usuário que trabalhou no projeto.  

 O diagrama a seguir mostra a relação entre projetos e soluções e os itens que eles contêm logicamente.  

 ![Projetos e solução do Visual Studio](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Criando novos projetos  
 A maneira mais fácil de criar um novo projeto é começar com um modelo de projeto, que consiste em um conjunto básico de arquivos de código, arquivos de configuração, configurações e ativos gerados previamente que permitem criar um tipo específico de aplicativo ou site em uma linguagem de programação específica. Esses modelos são os exibidos na caixa de diálogo **Novo Projeto** ou **Novo Site** quando você escolhe **Arquivo**, **Novo**, **Projeto** ou **Arquivo**, **Novo**, **Site da Web**. Para obter mais informações, consulte [Criando soluções e projetos](../ide/creating-solutions-and-projects.md).  

Também é possível criar modelos de item e de projeto personalizados. Para obter mais informações, consulte [Criando modelos de item e de projeto](../ide/creating-project-and-item-templates.md).  

## <a name="managing-projects-in-solution-explorer"></a>Gerenciamento de projetos no Gerenciador de Soluções  
 Depois de criar um novo projeto, você usa o **Gerenciador de Soluções** para exibir e gerenciar projetos e soluções e seus itens associados. A ilustração a seguir mostra o Gerenciador de Soluções com uma solução em C# que contém dois projetos.  

 ![Gerenciador de Soluções](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>Nesta seção  

-   [Criando soluções e projetos](../ide/creating-solutions-and-projects.md)  

-   [Adicionando e removendo itens de projeto](../ide/adding-and-removing-project-items.md)  

-   [Gerenciando propriedades do projeto e da solução](../ide/managing-project-and-solution-properties.md)  

-   [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)  

-   [Propriedades do aplicativo](../ide/application-properties.md)  

-   [Gerenciando assinatura de assembly e de manifesto](../ide/managing-assembly-and-manifest-signing.md)  

-   [Como especificar um ícone do aplicativo (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Direcionando a uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Consulte também  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
