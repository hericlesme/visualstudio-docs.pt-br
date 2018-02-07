---
title: "Gerar um campo, propriedade ou local - Geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 766311f0ba165c87e61bb873baa3ab2f0b2d1402
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Gerar um campo, propriedade ou local no Visual Basic
**O quê:** permite gerar imediatamente o código para um campo, propriedade ou local não declarada anteriormente. 

**Quando:** você introduz um novo campo, propriedade ou local durante a digitação e quer declará-la correta e automaticamente.  

**Por quê:** você poderia declarar o campo, propriedade ou local antes de usá-lo; no entanto, esse recurso gerará a declaração ou o tipo automaticamente. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um campo, local ou propriedade que ainda não existe.

   ![Código realçado](media/field-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Gerar variável ' *Name*' > Gerar campo/propriedade/local** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione **Ações Rápidas e Refatorações** e selecione **Gerar variável ' *Name*' > Gerar campo/propriedade/local** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da geração de campo/propriedade/local](media/field-preview-vb.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O campo, propriedade ou local será criado automaticamente com o tipo inferido a partir de seu uso.

   ![Resultado da geração de campo/propriedade/local](media/field-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)