---
title: "Gerar comentários da documentação XML - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>Gerar comentários da documentação XML em C# #
**O quê:** permite gerar imediatamente o XML básico necessário para documentar o elemento selecionado. 

**Quando:** você quer criar um Comentário do Documento XML para processamento posterior por uma ferramenta de documentação como Sandcastle.

**Por quê:** você poderia criar manualmente o bloco de comentário inteiro por conta própria, mas isso poupará tempo e aumentará a precisão ao gerar o modelo básico e os elementos adicionais. 

**Como:**

1. coloque o cursor de texto acima do elemento que você deseja documentar, por exemplo, um método.

   ![Método para documento](media/doc-highlight-cs.png)

1. Em seguida, digite **///** (3 aspas simples) que criará automaticamente o modelo básico e todos os elementos adicionais conforme o necessário.  Por exemplo, ao comentar um método, ele gerará as marcas **\<resumo\>**, além da marca **\<param\>** para cada parâmetro que é passado para o método e uma marca **\<return\>** para documentar o que o método retorna.

   ![Modelo](media/doc-preview-cs.png)

1. Conclua os comentários e adicione outras informações que você julgar necessárias.

   ![Comentário concluído](media/doc-result-cs.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Comentários de documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
