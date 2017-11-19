---
title: "Renomeie - a refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 60e2a623-b56d-4591-93dc-e51429e4e1ba
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: CSharp
ms.openlocfilehash: c89aae8e6e0f43ee2083bba46f2bbeeadd488535
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="rename-a-code-symbol-in-c"></a>Renomear um símbolo de código em c# #
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

   ![Renomear animação](media/rename_animated.gif)

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) salvando antes, usando as caixas de seleção no **Renomear** caixa que aparece na parte superior direita do seu IDE.

1. Quando estiver satisfeito com a alteração, clique no **aplicar** botão ou pressione **Enter** e as alterações serão confirmadas.

> [!NOTE]
> Se você usar um nome que já existe e que causa um conflito, a **Renomear** caixa em seu IDE irá avisá-lo.
>
> ![Renomeie o conflito](media/rename_conflict.png)

## <a name="see-also"></a>Consulte também  
[Refatoração (C#)](../refactoring-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)
