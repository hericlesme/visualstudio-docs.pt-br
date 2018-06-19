---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3373f1e1a23ae0373a9c49a39a924398ebe143e0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704766"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra toda a atividade no arquivo de log para resolução de problemas. Este arquivo aparece depois de você chamar `devenv /log` pelo menos uma vez. Por padrão, o arquivo de log é:

 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml

 em que *Versão* é a versão do Visual Studio. No entanto, você pode especificar um caminho e um nome de arquivo diferentes.

## <a name="syntax"></a>Sintaxe

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Comentários
 Essa opção deve aparecer no fim da linha de comando, depois de todas as outras opções.

 O log é gravado em todas as instâncias do Visual Studio que você invocou com a opção /log. As instâncias de log do Visual Studio que você invocou sem a opção não são registradas.

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)