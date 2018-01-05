---
title: "Implementar uma interface - geração de código (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e0b8df77e82ada8197b89fcdf451e4234a43669f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="implement-an-interface-in-c"></a>Implementar uma interface em c# #
**O que:** permite gerar imediatamente o código necessário para implementar uma interface. 

**Quando:** você deseja herdar de uma interface.  

**Motivo:** pode implementar manualmente todas as interfaces um por um, no entanto, esse recurso gerará automaticamente todas as assinaturas de método. 

**Como:**

1. Coloque o cursor na linha em que há um rabisco vermelho, indicando que você referenciou uma interface, mas não implementou todos os membros necessários.

   ![Código realçado](media/interface_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **implementar interface (explicitamente)** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **implementar interface (explicitamente)** do popup da janela de visualização.
     * Passe o mouse sobre o Rabisco vermelho e clique no ![Lâmpada](media/bulb.png) ícone que aparece.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

   ![Visualização da classe de implementação](media/interface_preview.png)

   >[!TIP]
   >Use o [ **visualizar alterações** ](../../ide/preview-changes.md) link na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.
   >
   >Além disso, você pode usar o **documento**, **projeto**, e **solução** links na parte inferior da janela de visualização para criar as assinaturas de método correto em várias classes que implementam a interface.

1. Assinaturas de método da interface será criado automaticamente, pronto para ser implementada.

   ![Implementar o resultado de classe](media/interface_result.png)

   >[!TIP]
   >Use o **implementar interface explicitamente** gerado de opção para iniciar cada método com o nome da interface para evitar colisões de nome.
   >
   >![Implementar interface explicitamente resultados](media/interface_explicitresult.png); 

## <a name="see-also"></a>Consulte também  
[Geração de código (C#)](../code-generation-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)  
