---
title: -Setup (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 296b33a5582f9a7ba9ed9540b90444376ead91be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
Força o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a mesclar os metadados de recursos que descrevem menus, barras de ferramentas e grupos de comando de todos os VSPackages disponíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Comentários  
 Esta opção não aceita nenhum argumento. O comando `devenv /setup` geralmente é fornecido como a última etapa do processo de instalação. Usar a opção `/setup` não inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 É necessário executar `devenv` como administrador para usar as opções [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra a última etapa na instalação de uma versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que inclui os VSPackages.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)