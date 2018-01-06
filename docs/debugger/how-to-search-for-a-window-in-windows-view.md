---
title: "Como: procurar uma janela no modo de exibição do Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dfec3f78e9f95a55d453c45c5a264125152cbf1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Como procurar uma janela na exibição de janelas
Você pode procurar uma janela específica no modo de exibição do Windows usando seu identificador, legenda, classe ou uma combinação de suas legenda e a classe como critério de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrará os atributos da janela selecionada na árvore de janela.  
  
 Comece com a árvore expandida para o segundo nível (todos os windows que são filhos da área de trabalho), para que você possa identificar windows de nível de área de trabalho por seu nome de classe e o título. Depois de ter escolhido uma janela de nível de área de trabalho, você pode expandir esse nível para encontrar uma janela filho específicos.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Para procurar uma janela no modo de exibição do Windows  
  
1.  Organizar as janelas assim que Spy + +, o [exibição Windows](../debugger/windows-view.md) janela e a janela de destino estão visíveis.  
  
2.  Do **pesquisa** menu, escolha **encontrar janela**.  
  
     O [caixa de diálogo de pesquisa de janela](../debugger/window-search-dialog-box.md) é aberto.  
  
    > [!TIP]
    >  Para reduzir a desordem, selecione o **Spy ocultar** opção. Esta opção oculta a janela principal do Spy + + e deixa somente o **pesquisa de janela** caixa de diálogo visível na parte superior de outros aplicativos. A janela principal do Spy + + é restaurada quando você clicar em **Okey** ou **Cancelar**, ou quando você desmarca o **ocultar Spy + +** opção.  
  
3.  Arraste o **ferramenta localizador** sobre a janela de destino. Quando você arrasta a ferramenta, o **pesquisa de janela** caixa de diálogo exibe detalhes sobre a janela selecionada.  
  
     - ou –  
  
     Se você souber o identificador da janela que você deseja (por exemplo, do depurador), você pode digitar no **tratar** caixa.  
  
     - ou –  
  
     Se você souber que a legenda e/ou classe da janela que você deseja, você pode digitá-los a **legenda** e **classe** caixas de texto e desmarque o **tratar** caixa de texto.  
  
4.  Escolha **backup** ou **para baixo** para a direção inicial da pesquisa.  
  
5.  Clique em **OK**.  
  
     Se uma janela correspondente for encontrada, ele é realçado no [exibição Windows](../debugger/windows-view.md) janela.