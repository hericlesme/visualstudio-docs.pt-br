---
title: Adicionar nós de resultados de pesquisa do XML esquema conjunto no espaço de trabalho
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9b260c6b0e63801134c3f15eabab5b13e2926e2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Como: Para adicionar nós de resultados de pesquisa de esquema para o espaço de trabalho

Este tópico explica como adicionar os nós que são realçadas em XML Schema Explorer como resultado de uma pesquisa de palavra-chave no espaço de trabalho.

> [!NOTE]
> Somente nós globais podem ser adicionados para o [espaço de trabalho](../xml-tools/xml-schema-designer-workspace.md).


 Este exemplo usa o exemplo [esquema de ordem de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Para adicionar nós definidos do resultado de esquema

1.  Siga as etapas em [como: criar e editar um arquivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Digite "purchaseOrder" na caixa de texto de pesquisa do [XML Explorer](../xml-tools/xml-schema-explorer.md) barra de ferramentas e clique no botão de pesquisa.

     ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Os resultados de pesquisa são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical.

3.  Adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.

     ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     O `purchaseOrder` nó e o `PurchaseOrderType` nó aparecer ao lado do outro na superfície de design do [exibição de gráfico](../xml-tools/graph-view.md). Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.