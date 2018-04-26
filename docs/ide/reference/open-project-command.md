---
title: Comando Abrir Projeto
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09241e72119a0a0973995b16152941bbe5272c3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="open-project-command"></a>Comando Abrir Projeto
Abre um projeto existente.

## <a name="syntax"></a>Sintaxe

```
File.OpenProject filename
```

## <a name="arguments"></a>Arguments
 `filename`

 Necessário. O nome de arquivo e caminho completo do projeto a abrir.

 A sintaxe para o argumento `filename` requer que os caminhos que contêm espaços usem aspas.

## <a name="remarks"></a>Comentários
 O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.

 Esse comando não está disponível durante a depuração.

## <a name="example"></a>Exemplo
 Este exemplo abre o projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], Test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)