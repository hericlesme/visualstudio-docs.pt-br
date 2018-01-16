---
title: "Opção de configuração devenv.exe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f03de74540d130d66ce123b355691e0828b93e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

A opção /Setup faz com que o Visual Studio mescle os metadados de recursos que descrevem menus, barras de ferramentas e grupos de comando de todos os VSPackages disponíveis.

## <a name="syntax"></a>Sintaxe

```
devenv /setup
```

## <a name="remarks"></a>Comentários

Esta opção não aceita nenhum argumento. O comando `devenv /setup` geralmente é fornecido como a última etapa do processo de instalação. O uso da opção `/setup` não inicia o Visual Studio.

É necessário executar `devenv` como administrador para usar as opções [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md).

## <a name="example"></a>Exemplo

Este exemplo mostra a última etapa na instalação de uma versão do Visual Studio que inclui VSPackages.

```
devenv /setup
```

## <a name="see-also"></a>Consulte também

[Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)