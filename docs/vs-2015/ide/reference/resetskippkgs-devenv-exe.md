---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e03e260662330556bff8f15a83fe747c374154b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475010"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [- ResetSkipPkgs (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetskippkgs-devenv-exe).  
  
  
Limpa todas as opções para ignorar o carregamento adicionadas a VSPackages por usuários que desejam evitar o carregamento de VSPackages com problemas, e inicia o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>Comentários  
 A presença de uma marcação SkipLoading desabilita o carregamento de um VSPackage; limpar a marcação habilita novamente o carregamento do VSPackage.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir limpa todas as marcas SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)



