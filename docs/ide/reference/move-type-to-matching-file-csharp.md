---
title: "Mover o tipo para o arquivo correspondente - Refatoração (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 4b7b9b1ba52bed5d2bdf042db0149d799c489a7d
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>Mover o tipo para um arquivo correspondente em C# #

**O quê:** permite mover o tipo selecionado para um arquivo separado com o mesmo nome.

**Quando:** você tem várias classes, structs, interfaces, etc. no mesmo arquivo que deseja separar.

**Por quê:** colocar vários tipos no mesmo arquivo pode dificultar a localização desses tipos.  Ao mover os tipos de arquivos com o mesmo nome, o código torna-se mais legível e mais fácil de navegar.

**Como:**

1. realce ou coloque o cursor do texto dentro do nome do tipo para mover:

   ![Código realçado](media/movetype-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Mover o tipo para *TypeName*.cs** no pop-up da janela Visualização onde *TypeName* é o nome do tipo selecionado.
   * **Mouse**
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Mover o tipo para *TypeName*.cs** no pop-up da janela Visualização onde *TypeName* é o nome do tipo selecionado.

   O tipo será instantaneamente movido para um novo arquivo com esse nome dentro da sua solução.

   ![Resultado embutido](media/movetype-result-cs.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)