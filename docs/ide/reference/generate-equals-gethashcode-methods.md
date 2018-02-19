---
title: "Gerar substituições dos métodos Equals e GetHashCode em C# no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: dc380985231937073bff1cb9ce275c38eb70448f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
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
     - Pressione **Ctrl +.** para acionar o menu **Ações e Refatorações Rápidas**.
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

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
