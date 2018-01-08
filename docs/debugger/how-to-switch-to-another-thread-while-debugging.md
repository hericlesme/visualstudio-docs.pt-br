---
title: "Como: alternar para outro Thread durante a depuração | Microsoft Docs"
ms.custom: 
ms.date: 04/27/2017
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
helpviewer_keywords: threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0710bad95484ada62faa042edabf5b76ac459558
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Como: alternar para outro Thread durante a depuração no Visual Studio
Quando você depurar um aplicativo multithread, você pode usar qualquer um dos vários métodos para alternar da thread que você estava trabalhando para outro thread.

> [!NOTE]
> Se você quiser controlar a ordem na qual os threads são executados, você precisa [congelar e descongelar threads](../debugger/get-started-debugging-multithreaded-apps.md).

Quando você examinar threads no editor de códigos e janelas de depuração multithread diferentes, a seta amarela indica o thread atual. Uma seta verde com uma chave final indica que um thread atual não tem o contexto atual do depurador.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Para alternar para qualquer thread que aparece 
  
-   No **Threads** ou **inspeção paralela** janela, clique duas vezes o thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para alternar para um thread em uma janela de origem  
  
-   Na medianiz esquerda, clique em um ícone de marcador de thread ![marcador de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker"), aponte para **alternar para**e, em seguida, clique no nome do thread para o qual você deseja alternar . O menu de atalho mostra apenas os threads nesse local específico.  
  
     Se nenhum marcadores de thread aparecerem, clique no **Threads** janela e verifique **Mostrar Threads na origem** está selecionado.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para alternar para um thread na barra de ferramentas do Local de Depuração  
  
1.  Sobre o **local do depurador** barra de ferramentas, clique no **Thread** lista.  
  
2.  Na lista, clique no thread para o qual você deseja alternar.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
