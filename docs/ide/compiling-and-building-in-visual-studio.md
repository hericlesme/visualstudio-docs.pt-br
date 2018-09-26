---
title: Compilando e criando no Visual Studio
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7ee37ddd9899b979d8440202c89d03284b26f48
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279070"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilar e criar no Visual Studio

Executar um build cria assemblies e aplicativos executáveis do código-fonte a qualquer momento durante um ciclo de desenvolvimento. De modo geral, o processo de compilação é muito semelhante entre vários tipos de projeto diferentes, como Windows, ASP.NET, aplicativos móveis e outros. O processo de compilação também é muito semelhante entre linguagens de programação, como C#, Visual Basic, C++ e F#.

Compilando seu código com frequência, é possível identificar erros rapidamente em tempo de compilação, como sintaxe incorreta, palavras-chave com erros de ortografia e erros de digitação. Também é possível detectar e corrigir com rapidez erros em tempo de execução, como erros lógicos e semânticos, compilando e executando frequentemente versões de depuração do código.

Uma compilação bem-sucedida é, essencialmente, uma validação de que o código-fonte do aplicativo contém sintaxe correta e de que todas as referências estáticas a bibliotecas, assemblies e outros componentes foram resolvidas. Isso produz um executável de aplicativo que pode, por sua vez, ser testado quanto ao funcionamento adequado em um [ambiente de depuração](../debugger/index.md) e por meio de uma variedade de testes manuais e automatizados para [validar a qualidade do código](../test/improve-code-quality.md). Após o aplicativo ter sido totalmente testado, você pode compilar uma versão de lançamento para ser implantada por seus clientes. Para obter uma introdução a esse processo, veja [Passo a passo: Criação de um aplicativo](../ide/walkthrough-building-an-application.md).

Você pode usar qualquer um dos métodos a seguir para compilar um aplicativo: o IDE do Visual Studio, as ferramentas de linha de comando do MSBuild, o Team Foundation Build e o Azure DevOps Services:

| Método de build | Benefícios |
| --- |--- | --- |
| IDE |– Criar compilações imediatamente e testá-las em um depurador.<br />– Executar builds em multiprocessador para projetos C++ e C#.<br />– Personalizar diferentes aspectos do sistema de build. |
| Linha de comando do MSBuild| – Criar projetos sem instalar o Visual Studio.<br />– Executar builds em multiprocessador para todos os tipos de projeto.<br />– Personalizar a maioria das áreas do sistema de build.|
| Compilação do Team Foundation | – Automatizar o processo de build como parte de um pipeline de integração contínua/entrega contínua.<br />– Aplicar testes automatizados com cada compilação.<br />– Empregar recursos baseados em nuvem praticamente ilimitados para processos de build.<br />– Modificar o fluxo de trabalho de compilação e, conforme necessário, criar atividades de compilação para realizar tarefas profundamente personalizadas.|

A documentação nesta seção detalha mais o processo de compilação baseado no IDE. Para obter mais informações sobre os outros métodos, confira [MSBuild](../msbuild/msbuild.md) e [Azure Pipelines](/azure/devops/pipelines/index?view=vsts), respectivamente.

## <a name="overview-of-building-from-the-ide"></a>Visão geral da compilação no IDE

Quando você cria um projeto, o Visual Studio cria configurações de compilação padrão para o projeto e para a solução que contém o projeto.  Essas configurações definem a maneira como as soluções e os projetos são criados e implantados. Configurações de projeto, em particular, são exclusivas a uma plataforma de destino (por exemplo, o Windows ou Linux) e tipo de build (por exemplo, depuração ou lançamento). Você pode editar essas configurações como quiser e também pode criar suas próprias configurações, conforme necessário.

Para obter uma introdução à compilação com o IDE, veja [Passo a passo: Criação de um aplicativo](walkthrough-building-an-application.md).

Em seguida, consulte [Compilando e limpando projetos e soluções no Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) para saber mais sobre as personalizações de diferentes aspectos que você pode fazer no processo. As personalizações incluem [alterar diretórios de saída](how-to-change-the-build-output-directory.md), [especificar eventos de build personalizados](specifying-custom-build-events-in-visual-studio.md), [gerenciar dependências do projeto](how-to-create-and-remove-project-dependencies.md), [gerenciar arquivos de log de build](how-to-view-save-and-configure-build-log-files.md) e [suprimir avisos do compilador](how-to-suppress-compiler-warnings.md).

A partir daí, você pode explorar uma variedade de outras tarefas:
- [Compreender configurações de build](understanding-build-configurations.md)
- [Compreender plataformas de build](understanding-build-platforms.md)
- [Gerenciar propriedades de solução e de projeto](managing-project-and-solution-properties.md).
- Especificar eventos de build em [C#](how-to-specify-build-events-csharp.md) e [Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Definir opções de build](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilar vários projetos paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Consulte também

- [Criar (compilar) projetos de site](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
