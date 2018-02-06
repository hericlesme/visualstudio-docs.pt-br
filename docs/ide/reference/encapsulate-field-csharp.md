---
title: Refatorar um campo para uma propriedade em C# | Microsoft Docs
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 383f4e5bac2072b77d8e1d862cd4a1b859a57f7c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="encapsulate-a-field-in-c"></a>Encapsular um campo em C# #

**O quê:** permite que você transforme um campo em uma propriedade e atualize todos os usos desse campo a fim de usar a propriedade recém-criada.

**Quando:** você quer mover um campo para uma propriedade e atualizar todas as referências a esse campo.

**Por quê:** você quer conceder a outras classes o acesso a um campo, mas não quer que essas classes tenham acesso direto.  Ao encapsular o campo em uma propriedade, você pode escrever o código para verificar o valor que está sendo atribuído, por exemplo.

**Como:**

1. realce ou coloque o cursor do texto dentro do nome do campo para encapsular:

   ![Código realçado](media/encapsulate-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl+R**, em seguida, **Ctrl+E**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Encapsular campo** no pop-up da janela Visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Encapsular Campo**.
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Encapsular campo** no pop-up da janela Visualização.

   Seleção | Descrição
   --------- | -----------
   **Encapsular campo (e usar propriedade)** | Encapsula o campo com uma propriedade e atualiza todos os usos do campo a fim de usar a propriedade gerada
   **Encapsular campo (mas ainda usá-lo)** | Encapsula o campo com uma propriedade, mas não altera qualquer uso do campo

   A propriedade será criada imediatamente, e as referências ao campo serão atualizadas, se isso for selecionado.

   > [!TIP]
   > Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na janela pop-up para ver qual será o resultado antes de confirmá-lo.

   ![Resultado de encapsular a propriedade](media/encapsulate-result-cs.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)