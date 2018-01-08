---
title: "Mover o tipo de arquivo correspondente - refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e0b3fd-d1d9-4e3f-b0f6-9f8ffbbc6297
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 862c144c2319f6247a9fd38d7f71036a4ba090a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Tipo de movimentação para um arquivo correspondente no Visual Basic
**O que:** permite mover o tipo selecionado para um arquivo separado com o mesmo nome.

**Quando:** ter várias classes, estruturas, interfaces, etc. no mesmo arquivo que você deseja separar.  

**Motivo:** colocar vários tipos no mesmo arquivo pode dificultar localizar esses tipos.  Movendo os tipos de arquivos com o mesmo nome, o código se torna mais legível e mais fácil de navegar.

**Como:**

1. Realçar ou coloque o cursor do texto dentro do nome do tipo para mover:

   ![Código realçado](media/movetype_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **mover tipo para *TypeName*. vb** de pop-up janela de visualização onde *TypeName* é o nome do tipo selecionado.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **mover tipo para *TypeName*. vb** de pop-up janela de visualização onde  *TypeName* é o nome do tipo selecionado.

   O tipo será instantaneamente movido para um novo arquivo com esse nome dentro de sua solução.

   ![Resultados inline](media/movetype_result.png)

## <a name="see-also"></a>Consulte também
[Refatoração (Visual Basic)](../refactoring-vb.md)