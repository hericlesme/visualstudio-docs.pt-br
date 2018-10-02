---
title: -Command (devenv.exe) | Microsoft Docs
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
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e4ff0beb638e9cf5ea7a0e5f0f3330300cca6f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476092"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [-comando (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/command-devenv-exe).  
  
  
Executa o comando especificado depois de iniciar o IDE (ambiente de desenvolvimento integrado) do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Arguments  
 `CommandName`  
 Necessário. O nome completo de um comando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou seu alias, colocado entre aspas duplas. Para obter mais informações sobre comandos e a sintaxe de aliases, consulte [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Comentários  
 Após a conclusão da inicialização, o IDE executa o comando nomeado. Se você usar essa opção, o IDE não mostrará a Página Inicial do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] na inicialização.  
  
 Se um suplemento expor um comando, será possível usar essa opção para iniciar o suplemento por meio da linha de comando. Para obter mais informações, consulte [Como controlar suplementos usando o Gerenciador de Suplementos](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Exemplo  
 Esse exemplo inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e executa a macro Abrir Arquivos Favoritos automaticamente.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



