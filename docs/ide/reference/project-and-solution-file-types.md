---
title: Projeto e tipos de arquivo de solução
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3786d6f38e4f87aa05a51b0a6112613bda65e56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947593"
---
# <a name="project-and-solution-file-types"></a>Tipos de arquivos de projeto e de solução

O Visual Studio é compatível com muitos tipos de arquivos. Em uma instalação particular, os componentes instalados determinam quais tipos de arquivos têm suporte. Este tópico lista tipos de arquivo de solução e de projeto que têm suporte em algumas instalações típicas.

## <a name="solution-files-sln-and-suo"></a>Arquivos de solução (.sln e .suo)

O Visual Studio usa dois tipos de arquivos (.sln e .suo) para armazenar configurações para soluções. Esses arquivos, conhecidos coletivamente como arquivos de solução, fornecem ao Solution Explorer as informações necessárias para exibir uma interface gráfica para gerenciar seus arquivos.

|Extensão|Nome|Descrição|
|---------------|----------|-----------------|
|.sln|Solução do Visual Studio|Organiza projetos, itens de projeto e itens de solução na solução.|
|.suo|Opções do usuário da solução|Mantém o controle de personalizações no nível de usuário feitas no Visual Studio, como pontos de interrupção.|

## <a name="project-files"></a>Arquivos de projeto

Projetos podem conter vários tipos de arquivos diferentes. Por exemplo, arquivos de código C# têm uma extensão **.cs** e arquivos C++ têm uma extensão **.cpp**. Os recursos são armazenados em arquivos **.resx** e XAML em arquivos **.xaml**. Arquivos [App.config](../../ide/managing-application-settings-dotnet.md) contêm informações de aplicativo que não devem ser incluídas no código do aplicativo&mdash;como cadeias de conexão.

Para obter mais informações sobre tipos de arquivos em projetos do C++, confira [Tipos de arquivo criados para projetos do Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Consulte também

- [Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)