---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
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
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31fd7f52ad2be89a3e6a40a76948aea0d8cc8bfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464500"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [- Updateconfiguration (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/updateconfiguration-devenv-exe).  
  
  
Notifica o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para mesclar os pacotes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no sistema e verificar o cache MEF para as alterações.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] executa este comando automaticamente quando você instala um pacote VSIX. Você deve executar `devenv.exe /updateconfiguration` após a aplicação de patch em seus arquivos de modo que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] atualize o cache MEF. Isso permite que você avalie se a correção é adequada.  
  
## <a name="example"></a>Exemplo  
 A linha de comando a seguir faz com que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mescle os pacotes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no sistema e verifique o cache MEF para quaisquer eventuais alterações.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)



