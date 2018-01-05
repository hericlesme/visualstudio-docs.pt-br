---
title: "Continuando a execução após uma exceção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84ade967c00e33390402e16a1b2980277f89ed5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="continuing-execution-after-an-exception"></a>Continuando a execução depois de uma exceção
Quando o depurador interromperá a execução devido a uma exceção, você verá o **auxiliar de exceção**, por padrão. Se você tiver desabilitado o **auxiliar de exceção** no **opções** caixa de diálogo, você verá o **Exception Assistant** (c# ou Visual Basic) ou o **exceção**  caixa de diálogo (C++).  
  
 Quando o **auxiliar de exceção** aparecer, você pode tentar corrigir o problema que causou a exceção.
  
## <a name="managed-and-native-code"></a>Código gerenciado e nativo  
 No código gerenciado e nativo, você pode continuar a execução no mesmo thread após uma exceção sem tratamento. O **auxiliar de exceção** esvazia a pilha de chamadas para o ponto onde a exceção foi lançada.
  
## <a name="mixed-code"></a>Código misto  
 Se você atinge uma exceção não tratada ao depurar um código nativo misto e gerenciado, as restrições do sistema operacional impedem o desenrolar da pilha de chamadas. Se você tentar voltar a pilha de chamadas usando o menu de atalho, uma mensagem de erro explicará que o depurador não pode desenrolar de uma exceção não tratada exceto durante a depuração de código misto.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)