---
title: "Refatoração Extrair método - (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 44a5dd2da4cd19a532e8e6cc9f21ef48b2585fe4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-c"></a>Extrair um método em c# #
**O que:** permite transformar um fragmento de código em seu próprio método.

**Quando:** tiver um fragmento de código existente em um método que precisa ser chamado a partir de outro método.  

**Motivo:** você poderia copiar/colar esse código, mas que poderia levar a eliminação de duplicação.  É a melhor solução refatorar esse fragmento em seu próprio método que pode ser chamado gratuitamente por qualquer outro método.

**Como:**

1. Realce o código a ser extraído:

   ![Código realçado](media/extractmethod_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + M**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **extrair método** do popup da janela de visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Extrair método**.
     * O código e selecione **Refatorar > Extrair > Extrair método**.
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **extrair método** do popup da janela de visualização.

   O método será criado imediatamente.  A partir daqui, agora você pode renomear o método digitando o novo nome.

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) salvando antes, usando as caixas de seleção no **Renomear** caixa que aparece na parte superior direita do seu IDE.

   ![Renomeie o método](media/extractmethod_rename.png)

1. Quando estiver satisfeito com a alteração, clique no **aplicar** botão ou pressione **Enter** e as alterações serão confirmadas.

## <a name="see-also"></a>Consulte também  
[Refatoração (C#)](../refactoring-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)