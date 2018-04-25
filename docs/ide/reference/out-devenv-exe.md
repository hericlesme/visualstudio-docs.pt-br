---
title: -Out (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af8d41a8a401e3087845e6d698163626f120a52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Especifica um arquivo para armazenar e exibir erros quando você executa, compila, recompila ou implanta uma solução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Arguments  
 `FileName`  
 Necessário. O caminho e o nome do arquivo para receber erros ao compilar um arquivo executável.  
  
## <a name="remarks"></a>Comentários  
 Se for especificado um nome de arquivo não exista, o arquivo será criado automaticamente. Se o arquivo já existir, os resultados serão anexados ao conteúdo existente do arquivo.  
  
 Erros de build de linha de comando são exibidos na janela **Comando** e a exibição do Gerenciador de Soluções da Janela de **Saída**. Essa opção é útil se você estiver executando compilações autônomas e precisar ver os resultados.  
  
## <a name="example"></a>Exemplo  
 Este exemplo executa `MySolution` e grava os erros no arquivo `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)