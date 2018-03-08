---
title: "Opção devenv.exe InstallVSTemplates | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

A opção /InstallVSTemplates registra modelos de item ou de projeto localizados em *\<Caminho de instalação do Visual Studio>*\Common7\IDE\ProjectTemplates\ ou *\<Caminho de instalação do Visual Studio>*\Common7\IDE\ItemTemplates\ para que eles possam ser acessados por meio das caixas de diálogo **Novo Projeto** e **Adicionar Novo Item**.

> [!WARNING]
> Essa opção apenas é compatível com o desenvolvimento de parceiros do Visual Studio. É necessário executar o devenv como administrador para usar as opções [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md). Para obter mais informações sobre permissões, consulte [Permissões de usuário](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Sintaxe

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>Consulte também

[Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)