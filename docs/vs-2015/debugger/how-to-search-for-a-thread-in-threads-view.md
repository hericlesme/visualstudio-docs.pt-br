---
title: 'Como: pesquisar por um Thread na exibição de Threads | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 071b32a6f8947289d12ad8a402a316b1d174f65f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474788"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Como procurar um thread na exibição de threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: pesquisar por um Thread na exibição de Threads](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-thread-in-threads-view).  
  
Você pode procurar um segmento específico na exibição de Threads por meio de sua cadeia de caracteres de ID ou o módulo de thread como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrará os atributos de thread selecionado na árvore de thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para pesquisar por um thread na exibição de Threads  
  
1.  Organizar as janelas assim que Spy + + e um ativo [exibição de Threads](../debugger/threads-view.md) janela são visíveis.  
  
2.  Dos **pesquisa** menu, escolha **localizar Thread**.  
  
     O [caixa de diálogo de pesquisa de Thread](../debugger/thread-search-dialog-box.md) é aberta.  
  
3.  Como critérios de pesquisa, digite a ID do thread ou uma cadeia de caracteres do módulo.  
  
4.  Limpe todos os campos para o qual você deseja especificar valores.  
  
    > [!TIP]
    >  Para localizar todos os threads pertencentes a um módulo, desmarque a **Thread** nome de caixa de texto e o tipo de módulo na **módulo** caixa. Em seguida, use **Localizar próximo** para continuar a pesquisa de threads.  
  
5.  Escolher **para cima** ou **para baixo** para a direção inicial da pesquisa.  
  
6.  Clique em **OK**.  
  
 Se um thread correspondente for encontrado, ele é realçado na janela de exibição de Threads.



