---
title: Tipos de arquivo de projeto e solução | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d239a5e129f12c4521ba190674d84430f8f2e646
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
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

[Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)