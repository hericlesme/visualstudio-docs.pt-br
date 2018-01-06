---
title: "Gerar Equals e GetHashCode método substituições - geração de código (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ce415cd6b86d8a5bd9bc905f3bc6b395d06753f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Gerar Equals e GetHashCode método substituições em c# #

**O que:** permite gerar **é igual a** e **GetHashCode** métodos.

**Quando:** gerar essas substituições quando você tem um tipo que representa um "valor" que deve ser comparado em alguns campos, em vez de por local do objeto na memória.

**Motivo:** se você estiver implementando um tipo de valor, considere substituir o método Equals para obter melhor desempenho sobre a implementação padrão do método Equals em ValueType.

Se você estiver implementando um tipo de referência, considere substituir o método Equals se o tipo de aparência de um tipo base, como ponto, cadeia de caracteres, BigNumber e assim por diante.

Substitua o método GetHashCode para permitir que um tipo funcionar corretamente em uma tabela de hash. Leia mais orientação na [operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators).

**Como:**

1. Coloque o cursor na sua declaração de tipo.

   ![Código realçado](media/overrides_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **gerar Equals(object)** ou **gerar Equals e GetHashCode** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **gerar Equals(object)** ou **gerar Equals e GetHashCode** na janela de visualização pop-up.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o tipo de declaração.

   ![Gerar visualização de substituições](media/overrides_preview.png)

1. Escolha os membros que você deseja gerar os métodos de substituições para:

    ![Caixa de diálogo substituições de gerar](media/overrides_dialog.png)

    > [!TIP]
    > Você também pode optar por gerar operadores nessa caixa de diálogo usando as caixas de seleção abaixo da lista de membros.

1. O Equals e GetHashCode substituições serão geradas com implementações padrão automático.

   ![Gerar o resultado do método](media/overrides_result.png)

## <a name="see-also"></a>Consulte também

[Geração de código (C#)](../code-generation-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)
