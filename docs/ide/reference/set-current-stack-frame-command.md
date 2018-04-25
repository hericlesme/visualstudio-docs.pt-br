---
title: Definir o comando do registro de ativação atual | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8851530dec3e5e1a2c3e829c1508155a2dbda8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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