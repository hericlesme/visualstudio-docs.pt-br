---
title: Pesquisando o conjunto de esquema | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6bef5c0358ecdadb5f8f9aada4e69d748b3fa14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="searching-the-schema-set"></a>Procurando pelo conjunto de esquema
XML Schema Explorer permite que você procurar o esquema define as seguintes maneiras:  
  
-   Pesquisa de palavras-chave.  
  
-   Pesquisa Esquema- específica.  
  
## <a name="keyword-search"></a>Palavra-chave pesquisa  
 Executar pesquisas de palavra-chave inserindo uma subcadeia de caracteres no **SchemaSet pesquisa** caixa de texto da barra de ferramentas do Pesquisador de objetos de esquema XML.  
  
 ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML Schema Explorer procura o esquema definido pelo seguinte:  
  
-   Alguns atributos de `name` ou de `ref` que corresponderem a palavra-chave especificada. Isso permite que você encontrar elementos, atributos, tipos, e assim por diante por nome.  
  
-   Atributos de `schemaLocation` de incluem instruções.  
  
-   Atributos de `namespace` de instruções de importação.  
  
## <a name="schema-specific-search"></a>Pesquisar esquema específico  
 XML Schema Explorer também inclui as pesquisas internos que você pode acessar usando o menu de contexto XML Schema Explorer. Para obter mais informações sobre menus de contexto disponíveis, consulte [Menus de contexto](../xml-tools/context-menus-xml-schema-explorer.md). Você também pode executar uma pesquisa específica do esquema de exibição início; Para obter mais informações, consulte a seção "Esquema definir detalhes" o [exibição início](../xml-tools/start-view.md) tópico.  
  
## <a name="displaying-and-navigating-search-results"></a>Exibindo e navegando resultados de pesquisa  
 Depois que a pesquisa é concluída, o painel de resultados de resumo é adicionado à barra de ferramentas com os resultados da pesquisa. Os resultados de pesquisa também são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical. Você pode navegar os resultados da pesquisa usando o **ir para próximo resultado da pesquisa** e **vá ao resultado da pesquisa anterior** botões no painel de resultados de resumo da barra de ferramentas XML Schema Explorer; usando as teclas de teclado F3 e Shift + F3; ou clicando na barra de rolagem, as marcas de escala.  
  
 Você pode adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.  
  
 ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Resultados da pesquisa de esclarecimento  
 Para limpar os resultados da pesquisa, clique o **x** botão no painel de resultados de resumo da barra de pesquisa do Gerenciador de esquema XML.  
  
## <a name="see-also"></a>Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)