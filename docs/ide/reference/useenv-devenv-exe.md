---
title: -UseEnv (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edcc80fe672a3829f8d5db4c9b1271e2cc687043
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)
Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e carrega variáveis de ambiente para o a caixa de diálogo **Diretórios VC++**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /useenv  
```  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e carrega variáveis de ambiente para a caixa de diálogo **Diretórios do VC++**.  
  
```  
Devenv.exe /useenv  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)