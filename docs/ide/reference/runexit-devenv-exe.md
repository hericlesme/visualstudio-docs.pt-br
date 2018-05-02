---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e2ce262b219b46d543389ac6a8ae8d71466419f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Compila e executa a solução ou o projeto especificado e, em seguida, fecha o IDE (ambiente de desenvolvimento integrado).

## <a name="syntax"></a>Sintaxe

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments
 `SolutionName`

 Necessário. O caminho completo e o nome de um arquivo de solução.

 `ProjectName`

 Necessário. O caminho completo e o nome de um arquivo de projeto.

## <a name="remarks"></a>Comentários
 Compila e executa o projeto ou a solução especificada de acordo com as configurações especificadas para a configuração da solução ativa. Essa opção minimiza o IDE enquanto o projeto ou a solução é executado, e fecha o IDE depois da conclusão da execução do projeto ou da solução.

-   Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

-   As informações de resumo, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/out`.

## <a name="example"></a>Exemplo
 Este exemplo executa a solução `MySolution` em um IDE minimizado usando a configuração de implantação ativa e, em seguida, fecha o IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)