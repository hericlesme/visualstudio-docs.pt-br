---
title: Operadores de pesquisa avançada em expressões de pesquisa | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24bf027f2fa480f95c0f223f8a319e7977615454
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468134"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operadores de pesquisa avançada em expressões de pesquisa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [operadores de pesquisa avançada em expressões de pesquisa](https://docs.microsoft.com/visualstudio/ide/advanced-search-operators-in-search-expressions).  
  
Usando operadores de pesquisa avançada, você pode refinar a pesquisa de conteúdo criando expressões de pesquisa mais complicadas com base em expressões mais simples. Como a tabela a seguir mostra, esses operadores restringem o contexto no qual uma consulta é executada.  
  
> [!WARNING]
>  Você precisa inserir os operadores de pesquisa avançada com dois pontos finais e nenhum espaço intermediário antes dos dois pontos para o mecanismo de pesquisa os reconheça.  
  
|Para pesquisar|Use|Exemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Um termo no título do tópico|título:|title:binaryreader|Tópicos que contêm "binaryreader" em seus títulos.|  
|Um termo em um exemplo de código|código:|code:readdouble|Tópicos que contêm "readdouble" em um exemplo de código.|  
|Um termo em um exemplo de uma linguagem de programação específica|code:vb:|code:vb:string|Tópicos que contêm "string" em um exemplo do Visual Basic.|  
|Um tópico associado a uma palavra-chave de índice específica|keyword:|keyword:readbyte|Tópicos associados à palavra-chave de índice "readbyte".|  
  
 Você pode usar o operador code: para encontrar conteúdo sobre qualquer uma das várias linguagens de programação, mas ele retorna resultados apenas para conteúdo marcado com uma linguagem de programação específica. A tabela a seguir lista as linguagens de programação que dão suporte a esse operador:  
  
|Linguagem de programação|Use|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> ou<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> ou<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> ou<br /><br /> code:c++<br /><br /> ou<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> ou<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> ou<br /><br /> code:js|  
|XAML|code:xaml|  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos em expressões de pesquisa](../ide/logical-operators-in-search-expressions.md)   
 [Dicas de pesquisa de texto completo](../ide/full-text-search-tips.md)



