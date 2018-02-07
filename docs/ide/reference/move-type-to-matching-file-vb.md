---
title: "Mover o tipo para o arquivo correspondente - Refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 510b984ad2de9476d53e9a5a4bcd667f393d3d4b
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Mover o tipo para um arquivo correspondente no Visual Basic

**O quê:** permite mover o tipo selecionado para um arquivo separado com o mesmo nome.

**Quando:** você tem várias classes, structs, interfaces, etc. no mesmo arquivo que deseja separar.  

**Por quê:** colocar vários tipos no mesmo arquivo pode dificultar a localização desses tipos.  Ao mover os tipos de arquivos com o mesmo nome, o código torna-se mais legível e mais fácil de navegar.

**Como:**

1. realce ou coloque o cursor do texto dentro do nome do tipo para mover:

   ![Código realçado](media/movetype-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Mover o tipo para *TypeName*. vb** no pop-up da janela Visualização onde *TypeName* é o nome do tipo selecionado.
   * **Mouse**
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Mover o tipo para *TypeName*.vb** no pop-up da janela Visualização onde *TypeName* é o nome do tipo selecionado.

   O tipo será instantaneamente movido para um novo arquivo com esse nome dentro da sua solução.

   ![Resultado embutido](media/movetype-result-vb.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)