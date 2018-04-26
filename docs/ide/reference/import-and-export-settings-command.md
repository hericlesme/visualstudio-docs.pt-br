---
title: Comando Importar e Exportar Configurações
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a95841d9b9b8e67f34883efcc1a55a2daba7e8b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="import-and-export-settings-command"></a>Comando Importar e Exportar Configurações
Importa, exporta ou redefine configurações [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintaxe

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Opções
 /export:`filename`

 Opcional. Exporta as configurações atuais para o arquivo especificado.

 /import:`filename`

 Opcional. Importa as configurações no arquivo especificado.

 /reset

 Opcional. Redefine as configurações atuais.

## <a name="remarks"></a>Comentários

Executar esse comando sem nenhuma opção abre o assistente **Importar e Exportar Configurações**. Para saber mais, confira [Sincronizar suas configurações](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Exemplo

O comando a seguir exporta as configurações atuais para o arquivo `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Consulte também

- [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)