---
title: -ResetSettings (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdec487781928c22a34e5e7586700ed0e91a31a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaura as configurações padrão do Visual Studio e inicia automaticamente o IDE do Visual Studio. Opcionalmente, redefine as configurações para um arquivo *vssettings* especificado.

As configurações padrão são determinadas pelo perfil selecionado quando o Visual Studio é iniciado pela primeira vez.

## <a name="syntax"></a>Sintaxe

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Arguments

`SettingsFile`

O caminho completo e o nome do arquivo *vssettings* a ser aplicado ao Visual Studio.

Para restaurar o perfil de Configurações Gerais de Desenvolvimento, use `General`.

## <a name="remarks"></a>Comentários

Se nenhum `SettingsFile` for especificado, será solicitado que você selecione uma coleção padrão de configurações na próxima vez que iniciar o Visual Studio.

## <a name="example"></a>Exemplo

A seguinte linha de comando aplica as configurações armazenadas no arquivo `MySettings.vssettings`.

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Consulte também

- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)