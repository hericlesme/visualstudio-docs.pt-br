---
title: "Como: procurar um processo no modo de exibição de processos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78c67ccc34d9c95914f6b46d537a4df3431c877f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Como procurar um processo na exibição de processos
Você pode procurar um processo específico no modo de exibição de processos por meio de sua cadeia de caracteres de ID ou o módulo de processo como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrará os atributos do processo selecionado na árvore de processo.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Para procurar um processo no modo de exibição de processos  
  
1.  Organizar as janelas assim que Spy + + e ativo [exibição processos](../debugger/processes-view.md) janela são visíveis.  
  
2.  Do **pesquisa** menu, escolha **encontrar processo**  
  
     O [caixa de diálogo de pesquisa de processo](../debugger/process-search-dialog-box.md) é aberto.  
  
3.  Digite a ID de processo ou uma cadeia de caracteres do módulo como critério de pesquisa.  
  
4.  Limpe todos os campos para os quais você não deseja especificar valores.  
  
    > [!TIP]
    >  Para localizar todos os processos pertencentes a um módulo, desmarque o **processo** caixa e digite o nome do módulo no **módulo** caixa. Em seguida, use **Localizar próximo** para continuar a pesquisa de processos.  
  
5.  Escolha **backup** ou **para baixo** para a direção inicial da pesquisa.  
  
6.  Clique em **OK**.  
  
 Se um processo de correspondência for encontrado, ele é realçado no **exibição de processo** janela.