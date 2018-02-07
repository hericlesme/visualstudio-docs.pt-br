---
title: "Extrair um método no Visual Basic | Microsoft Docs"
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
- vs.csharp.refactoring.extractmethod
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: f9e55a41f9a61626e8fce18cb11da6edc8a8bced
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="extract-a-method-in-visual-basic"></a>Extrair um método no Visual Basic

**O quê:** permite transformar um fragmento de código em seu próprio método.

**Quando:** você tem um fragmento de código existente em algum método que precisa ser chamado desde outro método.  

**Por quê:** você poderia copiar/colar esse código, mas que poderia levar à eliminação de duplicação.  A melhor solução é refatorar esse fragmento em seu próprio método, o que pode ser chamado livremente por qualquer outro método.

**Como:**

1. realce o código a ser extraído:

   ![Código realçado](media/extractmethod-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl+R**, em seguida, **Ctrl+M**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Extrair Método** no pop-up da janela Visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Extrair Método**.
     * Clique com o botão direito do mouse no código e selecione **Refatorar > Extrair > Extrair Método**.
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Extrair Método** no pop-up da janela Visualização.

   O método será criado imediatamente.  A partir daqui, agora você pode renomear o método digitando o novo nome.

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) antes de salvar usando as caixas de seleção na caixa **Renomear** que aparece na parte superior direita do seu IDE.

   ![Renomear método](media/extractmethod-rename-vb.png)

1. Quando estiver satisfeito com a alteração, clique no botão **Aplicar** ou pressione **Enter** e as alterações serão confirmadas.

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)