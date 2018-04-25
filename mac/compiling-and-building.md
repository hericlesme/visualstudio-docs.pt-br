---
title: Compilação e Criação no Visual Studio para Mac
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 7a7dfaeca45ae157dc9e82b9f8eff54244cbd7ca
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilação e criação no Visual Studio para Mac

O Visual Studio para Mac pode ser usado para compilar aplicativos e criar assemblies durante o desenvolvimento do seu projeto. É importante compilar e criar seu código antecipadamente e com frequência para poder identificar tipos incompatíveis e outros erros do tempo de compilação.

## <a name="building-from-the-ide"></a>Compilando no IDE

Usar o Visual Studio para Mac permite criar e executar builds imediatamente, fornecendo ainda controle sobre a funcionalidade de build. O Visual Studio para Mac usa o MSBuild como o sistema de build subjacente.

Todos os Projetos e Soluções criados no IDE terão uma configuração de build padrão, que define o contexto para builds. Essas configurações podem ser editadas ou você pode criar suas próprias. Criar ou modificar essas configurações atualizará automaticamente o arquivo de projeto, que é usado pelo MSBuild para compilar o projeto.  

Para obter mais informações sobre como compilar projetos e soluções no IDE, consulte o guia [Compilação e limpeza de Projetos e Soluções](~/building-and-cleaning-projects-and-solutions.md).

O Visual Studio para Mac também pode ser usado para fazer o seguinte:

* Alterar o caminho de saída. Isso é editado nas opções do Projeto:

    ![Alterar o caminho de saída](media/compiling-and-building-image4.png)

* Alterar o nível de detalhes da saída de build:

    ![Alterar o nível de detalhes de build](media/compiling-and-building-image5.png)

* Adicione comandos personalizados antes, durante ou depois da Compilação ou Limpeza:

    ![adicionar comandos personalizados](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Compilação na linha de comando

É possível usar o Microsoft Build Engine para compilar aplicativos por meio da linha de comando.

Consulte o conteúdo do [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild) para ver mais informações sobre como usar o MSBuild.

## <a name="building-from-visual-studio-team-services"></a>Como compilar com o Visual Studio Team Services

* [Compilar seu aplicativo Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Integração contínua com o Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)