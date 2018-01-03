---
title: "Definir o comando do registro de ativação atual | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3011b37cd7794745ce1700c412ccf227147728f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-stack-frame-command"></a>Comando Definir Quadro de Pilha Atual
Permite definir um registro de ativação específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Necessário. Seleciona um registro de ativação pelo seu índice.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)