---
title: "Refatorar uma assinatura de método em Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: daee27902bd602dfe1d67533ce45f42f44a3aba4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="change-a-method-signature-in-visual-basic"></a>Alterar a assinatura de um método em Visual Basic

**O quê:** permite remover ou alterar a ordem dos parâmetros do método.

**Quando:** você deseja mover ou remover um parâmetro de método que está sendo usado em uma variedade de locais.  

**Por quê:** você pode manualmente remover e reordenar os parâmetros e, em seguida, localizar todas as chamadas para esse método e alterá-las uma por uma, mas isso poderia levar a erros.  Essa ferramenta de refatoração executará a tarefa automaticamente.

**Como:**

1. realce ou coloque o cursor do texto dentro do nome do método para modificar, ou um de seus usos:

   ![Código realçado](media/changesignature-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl+R**, em seguida, **Ctrl+V**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Alterar Assinatura** no pop-up da janela Visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Remover Parâmetros**.
     * Selecione **Editar > Refatorar > Reordenar Parâmetros**.
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Alterar Assinatura** no pop-up da janela Visualização.

1. Na caixa de diálogo **Alterar Assinatura** que aparecer, você pode usar os botões à direita para alterar a assinatura do método:

   ![Caixa de diálogo Alterar Assinatura](media/changesignature-dialog-vb.png)

   | Botão | Descrição
   | ------ | ---
   | **Para cima/baixo** | Mova o parâmetro selecionado para cima e para baixo na lista
   | **Removerr**  | Remova o parâmetro selecionado da lista
   | **Restaurar** | Restaurar o parâmetro selecionado e riscado na lista

   > [!TIP]
   > Use a caixa de seleção [**Visualizar alterações de referência**](../../ide/preview-changes.md) para ver qual será o resultado antes de confirmá-lo.

1. Quando tiver terminado, pressione o botão **OK** para fazer as alterações.

   ![Resultado de Alterar Assinatura](media/changesignature-result-vb.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)