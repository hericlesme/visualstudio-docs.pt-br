---
title: Comando Set Current Thread | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 24a3f7d50d90769fe64b3657a0327eb8c96b7b42
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-thread-command"></a>Comando Definir Thread Atual
Define o thread especificado como o thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Necessário. Seleciona um thread por seu índice.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)