---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81c70c238a4503fbd05249ef6522cf020c00221c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="diff"></a>/Diff
Compara dois arquivos. As diferenças são exibidas em uma janela especial do Visual Studio.

## <a name="syntax"></a>Sintaxe

```
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Arguments
 `SourceFile`

 Necessário. O caminho completo e o nome do primeiro arquivo a ser comparado.

 `TargetFile`

 Necessário. O caminho completo e o nome do segundo arquivo a ser comparado

 `SourceDisplayName`

 Opcional. O nome de exibição do primeiro arquivo.

 `TargetDisplayName`

 Opcional. O nome de exibição do segundo arquivo.