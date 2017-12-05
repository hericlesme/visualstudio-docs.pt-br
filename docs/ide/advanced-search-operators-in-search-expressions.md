---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2017
---
title: "Operadores de pesquisa avançada em expressões de pesquisa | Microsoft Docs" ms.custom: "" ms.date: "06/02/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "artigo" helpviewer_keywords: 
  - "Help Viewer, pesquisando palavras-chave"
  - "Help Viewer, pesquisando código"
  - "Help Viewer, pesquisando código por linguagem de programação"
  - "Help Viewer, pesquisando títulos"
  - "pesquisando código [Help Viewer]"
  - "pesquisando títulos [Help Viewer]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operadores de pesquisa avançada em expressões de pesquisa
Ao usar operadores de pesquisa avançada no Help Viewer, você pode refinar sua pesquisa de conteúdo, especificando o local a procurar o termo da pesquisa em um tópico. A tabela a seguir descreve os quatro operadores de pesquisa avançada disponíveis.

|Para pesquisar|Use|Exemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Um termo no título do tópico|título:|title:binaryreader|Tópicos que contêm "binaryreader" em seus títulos.|  
|Um termo em um exemplo de código|código:|code:readdouble|Tópicos que contêm "readdouble" em um exemplo de código.|  
|Um termo em um exemplo de uma linguagem de programação específica|code:vb:|code:vb:string|Tópicos que contêm "string" em um exemplo de código do Visual Basic.|  
|Um tópico associado a uma palavra-chave de índice específica|keyword:|keyword:readbyte|Tópicos associados à palavra-chave de índice "readbyte".|  

> [!WARNING]
>  Você precisa inserir os operadores de pesquisa avançada com dois pontos finais e nenhum espaço intermediário antes dos dois pontos para o mecanismo de pesquisa os reconheça.    

## <a name="programming-languages-for-code-examples"></a>Linguagens de programação para exemplos de código
Você pode usar o operador code: para encontrar conteúdo sobre qualquer uma das várias linguagens de programação, mas ele retorna resultados apenas para conteúdo marcado com um rótulo de linguagem de programação. Para retornar exemplos de uma linguagem de programação específica, use um dos seguintes valores de linguagem de programação:  

|Linguagem de programação|Sintaxe do operador de pesquisa|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|code:xaml|
