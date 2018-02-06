---
title: "Gerar uma classe ou um tipo - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 87ef385a7e9edf9f975eb579bfab292039d60fa2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-class-or-type-in-c"></a>Gerar uma classe ou um tipo em C# #
**O quê:** permite gerar imediatamente o código para uma classe ou um tipo. 

**Quando:** você introduz uma nova classe ou tipo e deseja declará-lo correta e automaticamente.  

**Por quê:** você poderia declarar a classe ou o tipo antes de usá-lo; no entanto, esse recurso gerará a classe ou o tipo automaticamente. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou uma classe que ainda não existe.

   ![Código realçado](media/class-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar uma das opções no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione uma das opções no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Gerar visualização de classe](media/class-preview-cs.png)

   Seleção | Descrição
   --- | ---
   Gerar a classe '*TypeName*' no novo arquivo | Cria uma classe denominada *TypeName* em um arquivo chamado *TypeName*.cs/.vb
   Gerar a classe '*TypeName*' | Cria uma classe denominada *TypeName* no arquivo atual.
   Gerar classe aninhada '*TypeName*' | Cria uma classe denominada *TypeName* aninhada na classe atual.
   Gerar novo tipo... | Cria uma nova classe ou struct com todas as propriedades que você especificar.

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. Se você selecionar o item **Gerar novo tipo...**, uma caixa de diálogo será aberta para permitir executar algumas ações adicionais.

   ![Gerar tipo](media/class-newtype-cs.png)

   Seleção | Descrição
   --- | ---
   Acesso | Defina o tipo para ter acesso *Padrão*, *Interno* ou *Público*.
   Tipo | Isso pode ser definido como *classe* ou *struct*.
   Nome | Isso não pode ser alterado e será o nome que você já digitou.
   Projeto | Se houver vários projetos em sua solução, você poderá escolher onde deseja que a classe/struct viva.
   Nome do Arquivo | Você pode criar um novo arquivo ou pode adicionar o tipo a um arquivo existente.

1. A classe/struct será criada automaticamente com o construtor inferido a partir de seu uso.

   ![Gerar resultado de classe](media/class-result-cs.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)