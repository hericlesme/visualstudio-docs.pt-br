---
title: "Alterar assinatura do método - refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: b4f45f9d-9c8f-46ae-99f7-7705c6d90b6e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 6344a30b5772ffa23c09baa4f38a4478d907cc9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="change-a-method-signature-in-c"></a>Alterar uma assinatura de método em c# #
**O que:** permite que você remover ou alterar a ordem dos parâmetros do método.

**Quando:** você deseja mover ou remover um parâmetro de método que está sendo usado em uma variedade de locais.  

**Motivo:** você pode manualmente remover e reordenar os parâmetros e, em seguida, localizar todas as chamadas para esse método e alterá-los um por um, mas que poderiam levar a erros.  Essa ferramenta refatoração executará a tarefa automaticamente.

**Como:**

1. Realçar ou coloque o cursor do texto dentro do nome do método para modificar, ou um de seus usos:

   ![Código realçado](media/changesignature_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + V**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **alterar assinatura** do popup da janela de visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Remover parâmetros**.
     * Selecione **Editar > Refatorar > reordenar parâmetros**.
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **alterar assinatura** do popup da janela de visualização.

1. No **alterar assinatura** caixa de diálogo que aparecer, você pode usar os botões à direita para alterar a assinatura do método:

   ![Caixa de diálogo Alterar assinatura](media/changesignature_dialog.png)

   | Botão | Descrição
   | ------ | ---
   | **Para cima/baixo** | Mova o parâmetro selecionado para cima e lista
   | **Removerr**  | Remova o parâmetro selecionado da lista
   | **Restaurar** | Restaurar o parâmetro selecionado, riscado à lista

   > [!TIP]
   > Use o [ **visualizar alterações de referência** ](../../ide/preview-changes.md) caixa de seleção para ver qual será o resultado antes de confirmá-la.

1. Quando tiver terminado, pressione a **Okey** botão para fazer as alterações.

   ![Alterar o resultado de assinatura](media/changesignature_result.png)

## <a name="see-also"></a>Consulte também  
[Refatoração (C#)](../refactoring-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)