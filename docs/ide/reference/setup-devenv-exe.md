---
title: Opção de configuração devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942934"
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

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)