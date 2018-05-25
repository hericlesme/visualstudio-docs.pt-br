---
title: 'Como: obter uma visão geral de um conjunto de esquema usando o modo de exibição de gráfico no esquema XML Designer'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8be2666316bdc4d64d4f3dd4ec52c5104a1af5cc
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Como: obter uma visão geral de um esquema definido usando o modo de exibição de gráfico

Este tópico descreve como usar o [exibição de gráfico](../xml-tools/graph-view.md) para ver uma exibição de alto nível de nós em um conjunto de esquema e as relações entre os nós.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo

1.  Criar um novo arquivo de esquema XML e salve o arquivo como *Relationships.xsd*.

2.  Clique o **Use o Editor de XML para exibir e editar o arquivo de esquema XML subjacente** link no modo de exibição de iniciar.

3.  Copie o código de exemplo de esquema XML de [esquema XML de exemplo: relações](../xml-tools/sample-xsd-file-relationships.md) e cole-o para substituir o código que foi adicionado para o novo arquivo XSD por padrão.

4.  Clique em qualquer lugar no Editor de XML e selecione **Designer de exibição**.

5.  Selecione o modo de exibição de gráfico do **barra de ferramentas XSD**.

6.  Selecione **esquema definido** nó o **XML Schema Explorer** e arraste o nó para criar suface do modo de exibição de gráfico. Você deve ver todos os nós globais, e as setas que conectam os nós que possuem relações.

     ![Modo de exibição de gráfico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7.  Clique em qualquer nó na superfície de design e examine a barra de rastreamento para ver onde o nó selecionado é localizado no conjunto de esquema.

8.  Clique em qualquer nó de elemento em desing superfície e selecione **gerar XML de exemplo** para ver o documento de instância XML.