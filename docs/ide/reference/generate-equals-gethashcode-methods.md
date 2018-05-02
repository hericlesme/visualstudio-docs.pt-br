---
title: Gerar substituições dos métodos Equals e GetHashCode do C# no Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cdbb5273d046be8f11cc2fbc4a03ed6767a31e00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Gerar substituições dos métodos Equals e GetHashCode no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite que você gere os métodos **Equals** e **GetHashCode**.

**Quando:** gere essas substituições quando houver um tipo que precise ser comparado por um ou mais campos e não pelo local do objeto na memória.

**Por que:**

- Se você estiver implementando um tipo de valor, considere substituir o método **Equals** para aumentar desempenho em relação à implementação padrão do método Equals em ValueType.

- Se você estiver implementando um tipo de referência, considere substituir o método **Equals** se o seu tipo parecer um tipo base, como Point, String, BigNumber e assim por diante.

- Substitua o método **GetHashCode** para permitir que um tipo funcione corretamente em uma tabela de hash. Leia mais orientação em [operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Como fazer

1. coloque o cursor em sua declaração de tipo.

   ![Código realçado](media/overrides-highlight-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com a declaração de tipo.

   ![Visualização Gerar substituições](media/overrides-preview-cs.png)

1. Selecione **Gerar Equals(object)** ou **Gerar Equals e GetHashCode** no menu suspenso.

1. Na caixa de diálogo **Selecionar membros**, escolha os membros para os quais deseja gerar os métodos:

    ![Caixa de diálogo Gerar substituições](media/overrides-dialog-cs.png)

    > [!TIP]
    > Você também pode optar por gerar operadores nessa caixa de diálogo usando as caixas de seleção abaixo da lista de membros.

   As substituições de Equals e GetHashCode são geradas com implementações padrão.

   ![Resultado da geração do método](media/overrides-result-cs.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)