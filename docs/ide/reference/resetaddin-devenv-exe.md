---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f54e50e62b7f7f8f6dd1610904b66c82da02380
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Remove comandos e comando da interface do usuário associado ao Suplemento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Arguments  
 `AddIn`  
 Opcional. O nome de comando do Suplemento.  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o nome do comando do suplemento é igual a *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>* e aparece no Connect.cs como o parâmetro `commandName` do método `Exec`. Você também pode verificar o nome do comando começando a digitar o nome do suplemento na janela Comandos no Visual Studio e usando o IntelliSense para preencher o restante.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia o Visual Studio e impede o suplemento `MyAddin` de ser executado na inicialização.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)