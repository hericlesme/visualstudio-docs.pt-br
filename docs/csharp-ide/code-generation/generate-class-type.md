---
title: "Gerar uma classe ou tipo - geração de código (c#) | Microsoft Docs"
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
ms.openlocfilehash: b6825be5447718e47f7145b0b3b16ec6d0ee076c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-class-or-type-in-c"></a>Gerar uma classe ou um tipo em c# #
**O que:** permite gerar imediatamente o código para uma classe ou tipo. 

**Quando:** introduz uma nova classe ou tipo e deseja corretamente declará-la, automaticamente.  

**Motivo:** você pode declarar o tipo ou classe antes de usá-lo, no entanto, esse recurso será gerar a classe ou tipo automaticamente. 

**Como:**

1. Coloque o cursor na linha em que há um rabisco vermelho, indicando que você usou uma classe que ainda não existe.

   ![Código realçado](media/class_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione uma das opções do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione uma das opções do popup da janela de visualização.
     * Passe o mouse sobre o Rabisco vermelho e clique no ![Lâmpada](media/bulb.png) ícone que aparece.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

   ![Gerar visualização de classe](media/class_preview.png)

   Seleção | Descrição
   --- | ---
   Gerar a classe*TypeName*' no novo arquivo | Cria uma classe denominada *TypeName* em um arquivo chamado *TypeName*. cs/vb
   Gerar a classe*TypeName*' | Cria uma classe denominada *TypeName* do arquivo atual.
   Gerar classes aninhadas*TypeName*' | Cria uma classe denominada *TypeName* aninhados dentro da classe atual.
   Gere novo tipo... | Cria uma nova classe ou struct com todas as propriedades que você especificar.

   >[!TIP]
   >Use o [ **visualizar alterações** ](../../ide/preview-changes.md) link na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. Se você selecionar o **gerar novo tipo...**  item, uma caixa de diálogo será aberta que permite executar algumas ações adicionais.

   ![Gerar o tipo](media/class_newtype.png)

   Seleção | Descrição
   --- | ---
   Acesso | Defina o tipo ter *padrão*, *interno* ou *pública* acesso.
   Tipo | Isso pode ser definido como *classe* ou *struct*.
   Nome | Isso não pode ser alterado e será o nome que você já digitou.
   Projeto | Se houver vários projetos em sua solução, você pode escolher onde deseja que a classe/struct vida.
   Nome do Arquivo | Você pode criar um novo arquivo ou você pode adicionar o tipo para um arquivo existente.

1. O classe/struct será criado automaticamente com o construtor inferido a partir de seu uso.

   ![Gerar resultados de classe](media/class_result.png)

## <a name="see-also"></a>Consulte também  
[Geração de código (C#)](../code-generation-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)