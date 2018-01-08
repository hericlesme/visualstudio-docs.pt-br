---
title: "Parar a depuração na caixa de diálogo de progresso | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords: Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f98ce313228fd96b93cb52104b190adb057a712
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2018
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Caixa de diálogo Parar Depuração em Andamento
Essa caixa de diálogo aparece quando o depurador está tentando interromper uma sessão de depuração, mas parar a sessão deve demorar um pouco. Parar uma sessão de depuração normalmente é muito rápido e essa caixa de diálogo não é exibida. Entretanto, às vezes, leva mais tempo para desanexar de todos os processos que estão sendo depurados. Se parar a sessão levar mais do que alguns segundos (ou se ocorrer um erro de desanexação), essa caixa de diálogo será exibida. Se isso ocorrer com frequência, poderá ser devido a um problema interno e você deverá entrar em contato com o Product Support Services.  
  
 Você pode esperar que os processos para desanexar e essa caixa de diálogo desapareçam ou usar o **parar agora** botão para forçar o encerramento imediato.  
  
 **Parar agora**  
 Clique neste botão para encerrar imediatamente a sessão de depuração. Usando **parar agora** terminará em vez de desanexar os processos que está sendo depurados. Se você estiver depurando processos do sistema, encerrando os processos com **parar agora** pode ter efeitos inesperados e indesejados.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Desanexando programas](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)