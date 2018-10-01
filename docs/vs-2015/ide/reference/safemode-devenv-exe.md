---
title: -SafeMode (devenv.exe) | Microsoft Docs
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 308dd7e81a35604bcd0f6f5eba517b850ace17ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466983"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [- modo de segurança (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/safemode-devenv-exe).  
  
  
Inicia o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no modo de segurança, carregando apenas o ambiente e os serviços padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Comentários  
 Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] é iniciado, garantindo assim uma execução estável.  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir inicia o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no modo de segurança.  
  
## <a name="code"></a>Código  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)



