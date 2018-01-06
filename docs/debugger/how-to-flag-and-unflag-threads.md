---
title: 'Como: sinalizador e sinalizar Threads | Microsoft Docs'
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
helpviewer_keywords: treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 489403e4ce5052cb526a361e4548ab8823a20b18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flag-and-unflag-threads"></a>Como sinalizar não sinalizar threads
Você pode sinalizar um thread que você deseja dar atenção especial, marcando-o com um ícone de **Threads**, **pilhas paralelas** (exibição de thread), **inspeção paralela**e  **Threads de GPU** windows. Esse ícone pode ajudá-lo e a outros a distinguir threads sinalizados de outros threads.  
  
Threads sinalizados também recebem tratamento especial no **Thread** lista o **local do depurador** barra de ferramentas e em outras janelas depuração multithread. Você pode mostrar todos os threads ou somente threads sinalizados no **Thread** lista ou em outras janelas.
  
### <a name="to-flag-or-unflag-a-thread"></a>Para sinalizar ou remover sinalização de um thread 
  
-   No **Threads** ou **inspeção paralela** janela, localizar o thread que você está interessado e clique no ícone de sinalizador para marcar ou desmarcar o sinalizador. 
-   No **pilhas paralelas** janela, com o botão direito em um thread ou de um grupo de threads e selecione **sinalizador / <thread>**  ou **Unflag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>Para remover a sinalização de todos os threads  
  
-   No **Threads** janela, clique em qualquer thread e, em seguida, clique em **Remover Sinalizador de todos os Threads**.
-   No **inspeção paralela** janela, selecione todos os threads sinalizados, em seguida, clique com botão direito e selecione **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados  
  
-   Escolha o **Mostrar somente Threads sinalizados** botão em uma das janelas de depuração multithread.  
  
### <a name="to-flag-just-my-code"></a>Para sinalizar apenas meu código  
  
1.  Na barra de ferramentas na parte superior do **Threads** janela, clique no ícone de sinalizador.  
  
2.  Na lista suspensa, clique em **sinalizador apenas meu código**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para sinalizar os threads que estão associados com os módulos selecionados  
  
1.  Na barra de ferramentas do **Threads** janela, clique no ícone de sinalizador.  
  
2.  Na lista suspensa, clique em **sinalizar seleção de módulo personalizado**.  
  
3.  No **selecione módulos** caixa de diálogo, selecione os módulos que você deseja.  
  
4.  (Opcional) No **pesquisa** , digite uma cadeia de caracteres para pesquisa de módulos específicos.  
  
5.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Começar a depurar aplicativos multithread](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Passo a passo: Depurar aplicativos multithread usando a janela Threads](../debugger/how-to-use-the-threads-window.md)