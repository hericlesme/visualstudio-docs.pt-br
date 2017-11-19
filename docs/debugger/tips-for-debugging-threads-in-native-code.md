---
title: "Dicas para Threads em código nativo de depuração | Microsoft Docs"
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
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b0a2df03fdcb32e09824e37c26587912c542dea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Dicas para threads de depuração no código nativo
Veja algumas dicas que você pode usar durante a depuração de threads em código nativo:  
  
-   Você pode exibir o conteúdo do bloco de informações de Thread digitando `@TIB` no **inspecionar** janela ou **QuickWatch** caixa de diálogo.  
  
-   Você pode exibir o último código de erro para o thread atual inserindo `@Err` no **inspecionar** janela ou **QuickWatch** caixa de diálogo.  
  
-   As funções das bibliotecas em tempo de execução do C (CRT) podem ser úteis para depurar um aplicativo multithreaded. Para obter mais informações, consulte [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)