---
title: 'Como: sinalizar e remover sinalização de Threads | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f81de0353311d11cf744487d581296500d62ecb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464614"
---
# <a name="how-to-flag-and-unflag-threads"></a>Como sinalizar não sinalizar threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: sinalizador e remover sinalização de Threads](https://docs.microsoft.com/visualstudio/debugger/how-to-flag-and-unflag-threads).  
  
Você pode sinalizar um thread que você deseja dar atenção especial marcando-o com um ícone na **Threads**, **pilhas paralelas**, **inspeção paralela**, e **GPU Threads** windows. Esse ícone pode ajudá-lo e a outros a distinguir threads sinalizados de outros threads.  
  
 Threads sinalizados também recebem tratamento especial na **Thread** lista os **local de depuração** barra de ferramentas. Esta lista pode mostrar todos os threads ou apenas os sinalizados. Quando você sinaliza um thread, o **Thread** lista alterna automaticamente para mostrar somente threads sinalizados, mas você pode alternar para mostrar todos os threads conforme apropriado.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Para sinalizar ou desmarcar a sinalização de um thread usando a janela de threads  
  
-   No **Threads** janela, localize o thread que você está interessado e clique no ícone de sinalizador para marcar ou desmarcar o sinalizador.  
  
### <a name="to-unflag-all-threads"></a>Para remover a sinalização de todos os threads  
  
-   No **Threads** janela, clique em qualquer thread e, em seguida, clique em **Remover sinalização de todos os Threads**.  
  
### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados  
  
-   Escolha o botão de sinalizador na janela de depuração.  
  
### <a name="to-flag-just-my-code"></a>Para sinalizar apenas meu código  
  
1.  Na barra de ferramentas na parte superior do **Threads** janela, clique no ícone de sinalizador.  
  
2.  Na lista suspensa, clique em **sinalizar apenas meu código**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para sinalizar os threads que estão associados com os módulos selecionados  
  
1.  Na barra de ferramentas do **Threads** janela, clique no ícone de sinalizador.  
  
2.  Na lista suspensa, clique em **sinalizar seleção de módulo personalizado**.  
  
3.  No **selecionar módulos** caixa de diálogo, selecione os módulos desejados.  
  
4.  (Opcional) No **pesquisa** , digite uma cadeia de caracteres para pesquisar módulos específicos.  
  
5.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Passo a passo: depurando um aplicativo multi-threaded](../debugger/walkthrough-debugging-a-multithreaded-application.md)



