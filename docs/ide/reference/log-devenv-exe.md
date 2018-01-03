---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb84c4bab7ce9480deefbb88ac02289415f33d5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra toda a atividade no arquivo de log para resolução de problemas. Este arquivo aparece depois de você chamar `devenv /log` pelo menos uma vez. Por padrão, o arquivo de log é:  
  
 *%APPDATA%*\Microsoft\VisualStudio\\*Version*\ActivityLog.xml  
  
 em que *Versão* é a versão do Visual Studio. No entanto, você pode especificar um caminho e um nome de arquivo diferentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Comentários  
 Essa opção deve aparecer no fim da linha de comando, depois de todas as outras opções.  
  
 O log é gravado em todas as instâncias do Visual Studio que você invocou com a opção /log. As instâncias de log do Visual Studio que você invocou sem a opção não são registradas.  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)