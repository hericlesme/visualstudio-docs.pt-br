---
title: "Como: procurar um Thread na exibição de Threads | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a6aa48e8a83263ed31a36c97020a0f495a7a50f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Como procurar um thread na exibição de threads
Você pode procurar um segmento específico no modo de exibição de Threads por meio de sua cadeia de caracteres de ID ou o módulo de thread como critério de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrará os atributos do thread selecionado na árvore de thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para procurar por um thread na exibição de Threads  
  
1.  Organizar as janelas assim que Spy + + e ativo [exibição de Threads](../debugger/threads-view.md) janela são visíveis.  
  
2.  Do **pesquisa** menu, escolha **encontrar Thread**.  
  
     O [caixa de diálogo de pesquisa de Thread](../debugger/thread-search-dialog-box.md) é aberto.  
  
3.  Digite a ID do thread ou uma cadeia de caracteres do módulo como critério de pesquisa.  
  
4.  Limpe todos os campos para os quais você não deseja especificar valores.  
  
    > [!TIP]
    >  Para localizar todos os threads pertencentes a um módulo, desmarque o **Thread** nome de caixa de texto e o tipo de módulo no **módulo** caixa. Em seguida, use **Localizar próximo** para continuar a pesquisa de threads.  
  
5.  Escolha **backup** ou **para baixo** para a direção inicial da pesquisa.  
  
6.  Clique em **OK**.  
  
 Se um thread correspondente for encontrado, ele é realçado na janela de exibição de Threads.