---
title: "Gerar um campo, uma propriedade ou uma variável local no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 8de048928286017d4e6f79bda6aff804b49d3150
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Gerar um campo, uma propriedade ou uma variável local no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente o código para um campo, propriedade ou local não declarada anteriormente.

**Quando:** você introduz um novo campo, propriedade ou local durante a digitação e quer declará-la correta e automaticamente.

**Por quê:** você poderia declarar o campo, propriedade ou local antes de usá-lo; no entanto, esse recurso gerará a declaração ou o tipo automaticamente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica um campo, um local ou uma propriedade que ainda não existe.

   - C#:

    ![Código em C# realçado](media/field-highlight-cs.png)

   - Visual Basic:

    ![Código em VB realçado](media/field-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl +.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

    ![Visualização da geração de campo/propriedade/local](media/field-preview-cs.png)

1. Selecione uma das opções de geração no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   O campo, a propriedade ou o local é criado, com o tipo inferido de seu uso.

   - C#:

      ![Gerar o resultado do método C#](media/field-result-cs.png)

   - Visual Basic:

      ![Gerar o resultado do método VB](media/field-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
