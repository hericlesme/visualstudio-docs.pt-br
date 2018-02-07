---
title: "Substituições do método Gerar Equals e GetHashCode - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Substituições do método Gerar Equals e GetHashCode em C# #

**O quê:** Permite que você gere os métodos **Equals** e **GetHashCode**.

**Quando:** gere essas substituições quando você tiver um tipo que representa um "valor" que deveria ser comparado com relação a alguns campos, em vez do local do objeto na memória.

**Por quê:** se você estiver implementando um tipo de valor, considere substituir o método Equals para obter mais desempenho sobre a implementação padrão do método Equals em ValueType.

Se você estiver implementando um tipo de referência, considere substituir o método Equals se o seu tipo parecer um tipo base, como Point, String, BigNumber e assim por diante.

Substitua o método GetHashCode para permitir que um tipo funcione corretamente em uma tabela de hash. Leia mais orientação em [operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators).

**Como:**

1. coloque o cursor em sua declaração de tipo.

   ![Código realçado](media/overrides-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Gerar Equals(object)** ou **Gerar Equals e GetHashCode** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Gerar Equals(object)** ou **Gerar Equals e GetHashCode** no pop-up da janela Visualização.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com a declaração de tipo.

   ![Visualização Gerar substituições](media/overrides-preview-cs.png)

1. Escolha para quais membros você deseja gerar os métodos de substituição:

    ![Caixa de diálogo Gerar substituições](media/overrides-dialog-cs.png)

    > [!TIP]
    > Você também pode optar por gerar operadores nessa caixa de diálogo usando as caixas de seleção abaixo da lista de membros.

1. As substituições de Equals e GetHashCode serão geradas com implementações padrão automáticas.

   ![Resultado da geração do método](media/overrides-result-cs.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
