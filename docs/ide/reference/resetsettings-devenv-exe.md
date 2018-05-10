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
ms.openlocfilehash: 3c3d3a6ef558b510cfde716716daf97a549fbba4
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Restaura as configurações padrão do Visual Studio e inicia automaticamente o IDE do Visual Studio. Opcionalmente, redefine as configurações para um arquivo *vssettings* especificado.

As configurações padrão são determinadas pelo perfil selecionado quando o Visual Studio é iniciado pela primeira vez.

## <a name="syntax"></a>Sintaxe

```cmd
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

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Consulte também

- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)