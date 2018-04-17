---
title: 'Como: adicionar nós ao espaço de trabalho do XML Schema Explorer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d79aa5c10559eb67801ef68ad9b44f441736ccfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Como: Adicionar nós ao espaço de trabalho XML Schema Explorer
Este tópico explica como adicionar nós a [espaço de trabalho do Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md) do Gerenciador de esquema XML. Isso pode ser obtido arrastando e soltando-os nós XML Schema Explorer em uma exibição do designer XSD, ou usando o menu de contexto do gerenciador de esquema XML. Você também pode adicionar os nós que são realçadas como resultado de uma pesquisa executada por XML Schema Explorer. Para obter mais informações, consulte [como: adicionar esquema definido pesquisa resultados nós ao espaço de trabalho](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Somente nós globais podem ser adicionados para o [espaço de trabalho de Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para adicionar nós através do menu de contexto XML Explorer  
  
1.  Siga as etapas em [como: criar e editar um arquivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Clique com o botão direito do mouse no nó de `PurchaseOrderType` em um XSD Explorer. Selecione **Mostrar na exibição de gráfico**.  
  
     O nó de `purchaseOrderType` aparece na superfície de design do modo de gráfico.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastar e soltar sobre um nó para uma visualização  
  
1.  Clique com o botão direito do mouse no nó de `PurchaseOrderType` no modo de gráfico. Selecione **Mostrar em XML Schema Explorer**.  
  
     O nó é realçado em XML Schema Explorer.  
  
2.  Clique com o botão direito no `PurchaseOrderType` nó no Pesquisador de objetos de esquema XML e selecione **Mostrar todas as referências**.  
  
     O nó de `purchaseOrder` é realçado.  
  
3.  Arraste o nó de `purchaseOrder` sobre para o modo de exibição gráfico.  
  
     O nó de `purchaseOrder` e o nó de `PurchaseOrderType` aparecem próximos uns dos outros na superfície de design do modo de gráfico. Porque os dois nós realted (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para adicionar nós que usam o esquema Explorer pesquisam o recurso  
  
1.  Digite "purchaseOrder" na caixa de texto de pesquisa do [XML Explorer](../xml-tools/xml-schema-explorer.md) barra de ferramentas e clique no botão de pesquisa.  
  
     ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Os resultados de pesquisa são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical.  
  
2.  Adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.  
  
     ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     O `purchaseOrder` nó e o `PurchaseOrderType` nó aparecer ao lado do outro na superfície de design do [exibição de gráfico](../xml-tools/graph-view.md). Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.  
  
## <a name="see-also"></a>Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)