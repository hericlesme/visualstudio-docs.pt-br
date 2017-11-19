---
title: "Encapsular campo - refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.openlocfilehash: 9575ad83ead4960016ba7814642cacb1db04ea4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-visual-basic"></a>Encapsular um campo no Visual Basic
**O que:** permite transformar um campo em uma propriedade e atualizar todos os usos do campo para usar a propriedade recém-criado.

**Quando:** você deseja mover um campo em uma propriedade e atualizar todas as referências a esse campo.  

**Motivo:** você deseja conceder acesso de outras classes para um campo, mas não deseja que essas classes têm acesso direto.  Ao encapsular campo em uma propriedade, você pode escrever código para verificar o valor que está sendo atribuído, por exemplo.

**Como:**

1. Realçar ou coloque o cursor do texto dentro do nome do campo a encapsular:

   ![Código realçado](media/encapsulate_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + E**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **campo encapsular** entrada o popup da janela de visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > encapsular campo**.
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **campo encapsular** entrada o popup da janela de visualização.

   Seleção | Descrição
   --------- | -----------
   **Encapsular campo (e usar propriedade)** | Encapsula o campo com uma propriedade e atualiza todos os usos do campo para usar a propriedade gerada
   **Encapsular campo (mas ainda usar o campo)** | Encapsula o campo com uma propriedade, mas deixa todos os usos do campo inalterados

   A propriedade será criada imediatamente e referências ao campo serão atualizadas, se selecionado.

   > [!TIP]
   > Use o [ **visualizar alterações** ](../../ide/preview-changes.md) na janela pop-up para ver qual será o resultado antes de confirmá-la.

   ![Encapsular o resultado da propriedade](media/encapsulate_result.png)

## <a name="see-also"></a>Consulte também  
[Refatoração (Visual Basic)](../refactoring-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)