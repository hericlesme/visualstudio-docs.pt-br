---
title: "Opção de configuração devenv.exe | Microsoft Docs"
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37fe50eefc36e7b5396f396d2b614851a0bd9cb
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

A opção /Setup faz com que o Visual Studio mescle os metadados de recursos que descrevem menus, barras de ferramentas e grupos de comando de todos os VSPackages disponíveis.

## <a name="syntax"></a>Sintaxe

```shell
devenv /setup
```

## <a name="remarks"></a>Comentários

Esta opção não aceita nenhum argumento. O comando `devenv /setup` geralmente é fornecido como a última etapa do processo de instalação. O uso da opção `/setup` não inicia o Visual Studio.

> [!NOTE]
> Você deve executar `devenv` como administrador para usar a opção `/setup`.

## <a name="example"></a>Exemplo

Este exemplo mostra a última etapa na instalação de uma versão do Visual Studio que inclui VSPackages.

```shell
devenv /setup
```

## <a name="see-also"></a>Consulte também

[Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)