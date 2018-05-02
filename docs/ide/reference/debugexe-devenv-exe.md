---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 065648588b51ad6c71ae1a10235da4f096470abe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Abre o arquivo executável especificado a ser depurado.

## <a name="syntax"></a>Sintaxe

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Arguments
 `ExecutableFile`

 Necessário. O caminho e o nome de um arquivo .exe.

 Se o arquivo .exe não for encontrado ou não existir, nenhum aviso nem erro será exibido, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iniciará normalmente.

## <a name="remarks"></a>Comentários
 Quaisquer cadeias de caracteres após o parâmetro `ExecutableFile` são passadas para esse arquivo como argumentos.

## <a name="example"></a>Exemplo
 O exemplo a seguir abre o arquivo `MyApplication.exe` para depuração.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)