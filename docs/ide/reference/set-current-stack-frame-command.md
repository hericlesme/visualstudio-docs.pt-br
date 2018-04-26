---
title: Comando Definir Quadro de Pilha Atual
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 314ee2a7dec352f4bcdcf8e7d164950a422b79d2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="set-current-stack-frame-command"></a>Comando Definir Quadro de Pilha Atual
Permite definir um registro de ativação específico.

## <a name="syntax"></a>Sintaxe

```
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Arguments
 `index`

 Necessário. Seleciona um registro de ativação pelo seu índice.

## <a name="example"></a>Exemplo

```
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)