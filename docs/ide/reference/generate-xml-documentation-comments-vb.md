---
title: "Gerar comentários da documentação XML para o Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>Gerar comentários da documentação XML no Visual Basic

**O quê:** permite gerar imediatamente o XML básico necessário para documentar o elemento selecionado. 

**Quando:** você quer criar um Comentário do Documento XML para processamento posterior por uma ferramenta de documentação como Sandcastle.

**Por quê:** você poderia criar manualmente o bloco de comentário inteiro por conta própria, mas isso poupará tempo e aumentará a precisão ao gerar o modelo básico e os elementos adicionais. 

**Como:**

1. coloque o cursor de texto acima do elemento que você deseja documentar, por exemplo, um método.

   ![Método para documento](media/doc-highlight-vb.png)

1. Em seguida, digite **'''** (3 aspas simples) que criará automaticamente o modelo básico e todos os elementos adicionais conforme o necessário.  Por exemplo, ao comentar um método, ele gerará as marcas **\<resumo\>**, além da marca **\<param\>** para cada parâmetro que é passado para o método e uma marca **\<return\>** para documentar o que o método retorna.

   ![Modelo](media/doc-preview-vb.png)

1. Conclua os comentários e adicione outras informações que você julgar necessárias.

   ![Comentário concluído](media/doc-result-vb.png)

## <a name="see-also"></a>Consulte também

[Documentação do código com XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[Geração de código](../code-generation-in-visual-studio.md)