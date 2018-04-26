---
title: Comando Ir para
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b55e399dab41065fb96f9f3ac8e80484860f5187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="go-to-command"></a>Comando Ir para
Move o cursor para a linha especificada.

## <a name="syntax"></a>Sintaxe

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
 `linenumber`

 Opcional. Um inteiro que representa o número da linha para a qual ir.

## <a name="remarks"></a>Comentários
 A numeração de linha começa em um. Se o valor de `linenumber` for menor que um, a primeira linha será exibida. Se o valor de `linenumber` for maior que o número da última linha, a última linha será exibida.

 Se um valor para `linenumber` não for especificado, a caixa de diálogo **Ir para a Linha** será exibida.

 O alias para esse comando é GoToLn.

## <a name="example"></a>Exemplo

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)