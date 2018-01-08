---
title: "Renomeie - a refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: da85803adf3de8afa0912a1f47e2b474952df51d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Renomear um símbolo de código no Visual Basic
**O que:** permite renomear identificadores para símbolos de código, como campos, variáveis locais, métodos, namespaces, propriedades e tipos.

**Quando:** você deseja renomear algo a com segurança sem a necessidade de localizar todas as instâncias e copiar/colar o novo nome.  

**Motivo:** copiando e colando o novo nome em um projeto inteiro provavelmente resultar em erros.  Essa ferramenta refatoração com precisão executará a ação de renomeação.

**Como:**

1. Realçar ou coloque o cursor do texto dentro do item a ser renomeado:

   ![Código realçado](media/rename_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + R**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
   * **Mouse**
     * Selecione **Editar > Refatorar > Renomear**.
     * O código e selecione **Renomear**.

1. Renomear o item digitando o novo nome.

   ![Renomear animação](media/rename_rename.png)

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) salvando antes, usando as caixas de seleção no **Renomear** caixa que aparece na parte superior direita do seu IDE.

1. Quando estiver satisfeito com a alteração, clique no **aplicar** botão ou pressione **Enter** e as alterações serão confirmadas.

> [!NOTE]
> Se você usar um nome que já existe e que causa um conflito, a **Renomear** caixa em seu IDE irá avisá-lo.
>
> ![Renomeie o conflito](media/rename_conflict.png)

## <a name="see-also"></a>Consulte também  
[Refatoração (Visual Basic)](../refactoring-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)