---
title: "Apresentar uma variável local - geração de código (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3e68029ec1233eb5bc77ac21002fb7ce9befe98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="introduce-a-local-variable-in-c"></a>Apresentar uma variável local em c# #
**O que:** permite gerar imediatamente uma variável local para substituir uma expressão existente.

**Quando:** você tiver um código que pode ser facilmente reutilizado posteriormente se estivesse em uma variável local.  

**Motivo:** você pode copiar e colar o código várias vezes para usá-lo em vários locais, no entanto, seria melhor executar a operação uma vez, armazena o resultado em uma variável local e usar o throughought variável local. 

**Como:**

1. Realce a expressão que você deseja atribuir a uma nova variável local.

   ![Código realçado](media/local_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione  **introduzir local (todas as ocorrências da) '*expressão*' * * de pop-up janela de visualização onde *expressão* é o código realçado.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione  **introduzir local (todas as ocorrências da) '*expressão*' * * de pop-up janela de visualização onde *expressão* é o código realçado.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

   ![Introduzir visualização local](media/local_preview.png)

   >[!TIP]
   >Use o [ **visualizar alterações** ](../../ide/preview-changes.md) link na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. A variável local será criada automaticamente com o tipo inferido de seu uso.  Renomeie a nova variável local digitando-o.

   ![Apresentar resultados local](media/local_result.png)

   >[!NOTE]
   >Você pode usar o **.... All ocorrências de...**  opção de menu para substituir todas as ocorrências da expressão selecionada encontrado, não apenas aquele especificamente realçado.

## <a name="see-also"></a>Consulte também  
[Geração de código (C#)](../code-generation-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md) 
