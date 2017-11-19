---
title: "Gerar comentários da documentação XML - geração de código (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bf34acffb037369458aa4a86a5ecf629f127004
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-xml-documentation-comments-in-c"></a>Gerar comentários da documentação XML em c# #
**O que:** permite gerar imediatamente a base de dados de XML necessário para documentar o elemento selecionado. 

**Quando:** para criar um comentário de documento XML para processamento posterior por uma ferramenta de documentação como Sandcastle.

**Motivo:** você pode criar manualmente o bloco de comentário inteiro por conta própria, mas isso economizará tempo e aumentar a precisão ao gerar o modelo base e elementos adicionais. 

**Como:**

1. Coloque o cursor de texto acima do elemento que você deseja que o documento, por exemplo, um método.

   ![Método de documento](media/doc_highlight.png)

1. Em seguida, digite  **///**  (3 em diante barras) que cria automaticamente o modelo base e todos os elementos adicionais conforme necessário.  Por exemplo, quando um método de comentário, ele irá gerar o  **\<resumo\>**  marcas, bem como a  **\<param\>**  marca para cada parâmetro que é passado para o método e um  **\<retorna\>**  marca para documentar o método retorna.

   ![Modelo](media/doc_preview.png)

1. Conclua os comentários e adicionar qualquer informação adicional que você acha que é necessária.

   ![Comentário concluído](media/doc_result.png)

## <a name="see-also"></a>Consulte também
[Geração de código (C#)](../code-generation-csharp.md)  
[Comentários de documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
