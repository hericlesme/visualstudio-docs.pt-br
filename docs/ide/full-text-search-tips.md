---
redirect_url: /visualstudio/ide/how-to-search-for-topics
ms.openlocfilehash: a66c168ca81b22c32fc05afddd01266950791d1e
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2017
---
title: "Dicas de pesquisa de texto completo | Microsoft Docs" ms.custom: "" ms.date: "11/04/2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" f1_keywords: 
  - "hv_search" helpviewer_keywords: 
  - "Help Viewer, dicas de pesquisa de texto completo"
  - "dicas de pesquisa de texto completo [Help Viewer]" ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="full-text-search-tips"></a>Dicas de pesquisa de texto completo
Um dos métodos mais úteis para localizar informações na Ajuda é executando uma pesquisa de texto completo. Você pode criar pesquisas mais direcionadas, que retornam somente os tópicos mais interessantes, se você entender como a sintaxe afeta a consulta. A sintaxe inclui caracteres especiais, palavras reservadas e filtros. Este tópico fornece dicas, procedimentos e informações detalhadas de sintaxe para ajudá-lo a construir melhor suas consultas.
  
### <a name="general-guidelines"></a>Diretrizes gerais  
A tabela a seguir inclui algumas regras básicas e diretrizes para o desenvolvimento de consultas de pesquisa na Ajuda.  
  
|Sintaxe|Descrição|  
|------------|-----------------|  
|Diferenciação de maiúsculas e minúsculas|As pesquisas não diferenciam maiúsculas de minúsculas. Desenvolva seus critérios de pesquisa usando caracteres em maiúsculas ou em minúsculas. Por exemplo, "OLE" e "ole" retornam os mesmos resultados.|  
|Combinações de caracteres|Não é possível pesquisar somente por letras (a–z) ou números (0–9) individuais. Se você tentar pesquisar determinadas palavras reservadas, como "e", "de" e "com", elas serão ignoradas. Para obter mais informações, consulte "Palavras ignoradas em pesquisas (palavras irrelevantes)" posteriormente neste tópico.|  
|Ordem de avaliação|As consultas de pesquisa são avaliadas da esquerda para a direita.|  
  
### <a name="search-syntax"></a>Pesquisa de sintaxe  
 Se você especificar uma cadeia de caracteres de pesquisa que inclui várias palavras, como "word1 word2", essa cadeia de caracteres será equivalente a digitar "word1 AND word2", que retornará apenas os tópicos que contêm todas as palavras individuais nessa cadeia de caracteres de pesquisa.  
  
> [!IMPORTANT]
> - Não há suporte para pesquisas de frase. Se você especificar mais de uma palavra em uma cadeia de caracteres de pesquisa, os tópicos retornados conterão todas as palavras especificadas, mas não necessariamente a frase exata especificada.  
> - Use operadores lógicos para especificar a relação entre as palavras em sua frase de pesquisa. É possível incluir operadores lógicos como AND, OR, NOT e NEAR para refinar ainda mais a sua pesquisa. Por exemplo, se você pesquisar "declarando NEAR união", os resultados da pesquisa incluirão tópicos que contêm as palavras "declarando" e "união" com poucas palavras entre as duas. Para obter mais informações, consulte [Operadores lógicos em expressões de pesquisa](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filtros  
 É possível restringir ainda mais os resultados da pesquisa usando operadores de pesquisa avançada. A Ajuda inclui três categorias que você pode usar para filtrar os resultados de uma pesquisa de texto completo: Título, Código e Palavra-chave.
  
### <a name="ranking-of-search-results"></a>Classificação de resultados da pesquisa  
 O algoritmo de pesquisa é aplicável a determinados critérios para ajudar a classificar resultados da pesquisa superiores ou inferiores na lista de resultados. No geral:  
  
1.  O conteúdo que inclui palavras de pesquisa no título tem uma classificação mais alta do que o conteúdo que não inclui.  
  
2.  O conteúdo que inclui palavras de pesquisa muito próximas tem uma classificação mais alta do que o conteúdo que não inclui.  
  
3.  O conteúdo com uma densidade maior das palavras de pesquisa tem uma classificação mais alta do que o conteúdo que tem uma densidade menor das palavras de pesquisa.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Palavras ignoradas em pesquisas (palavras irrelevantes)  
 Palavras ou números que ocorrem com frequência, chamados de palavras irrelevantes, são automaticamente ignorados durante uma pesquisa de texto completo. Por exemplo, se você pesquisar a frase "passar por", os resultados da pesquisa exibirão tópicos que contêm a palavra "passar", mas não "por".  
  
## <a name="see-also"></a>Consulte também
[Localizar informações](../ide/locate-information.md)   
[Operadores lógicos em expressões de pesquisa](../ide/logical-operators-in-search-expressions.md)