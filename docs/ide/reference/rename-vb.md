---
title: "Renomeação de refatoração no Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f9421ed314dc513d5e8af30bad907766342300a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Renomear um símbolo de código no Visual Basic

**O quê:** permite renomear identificadores para símbolos de código, como campos, variáveis locais, métodos, namespaces, propriedades e tipos.

**Quando:** você deseja renomear algo com segurança sem a necessidade de localizar todas as instâncias e copiar/colar o novo nome.

**Por quê:** copiar e colar o novo nome em um projeto inteiro provavelmente resultaria em erros.  Essa ferramenta de refatoração realizará com precisão a ação de renomeação.

**Como:**

1. realce ou coloque o cursor do texto dentro do item a ser renomeado:

   ![Código realçado](media/rename-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl+R**, em seguida, **Ctrl+R**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
   * **Mouse**
     * Selecione **Editar > Refatorar > Renomear**.
     * Clique com o botão direito do mouse no código e selecione **Renomear**.

1. Renomeie o item digitando o novo nome.

   ![Renomear animação](media/rename-rename-vb.png)

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) antes de salvar usando as caixas de seleção na caixa **Renomear** que aparece na parte superior direita do seu IDE.

1. Quando estiver satisfeito com a alteração, clique no botão **Aplicar** ou pressione **Enter** e as alterações serão confirmadas.

> [!NOTE]
> Se você usar um nome que já existe e que poderia causar um conflito, a caixa **Renomear** em seu IDE irá avisá-lo.
>
> ![Conflito de renomeação](media/rename-conflict-vb.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)