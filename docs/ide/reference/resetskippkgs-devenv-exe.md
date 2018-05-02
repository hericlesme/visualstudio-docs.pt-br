---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Limpa todas as opções para ignorar o carregamento adicionadas a VSPackages por usuários que desejam evitar o carregamento de VSPackages com problemas, e inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintaxe

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Comentários
 A presença de uma marcação SkipLoading desabilita o carregamento de um VSPackage; limpar a marcação habilita novamente o carregamento do VSPackage.

## <a name="example"></a>Exemplo
 O exemplo a seguir limpa todas as marcas SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)