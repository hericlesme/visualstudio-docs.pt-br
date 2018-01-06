---
title: "Como: obter uma visão geral de um conjunto de esquema usando o modo de exibição de gráfico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9499e9972f32998b66be23d60acb8c585776d62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Como: Obter uma visão geral de um conjunto de esquema usando a exibição do gráfico
Este tópico descreve como usar o [exibição de gráfico](../xml-tools/graph-view.md) para ver uma exibição de alto nível de nós em um conjunto de esquema e as relações entre os nós.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo  
  
1.  Crie um novo arquivo de esquema XML e salve o arquivo como Relationships.xsd.  
  
2.  Clique o **Use o Editor de XML para exibir e editar o arquivo de esquema XML subjacente** link no modo de exibição de iniciar.  
  
3.  Copie o código de exemplo de esquema XML de [esquema XML de exemplo: relações](../xml-tools/sample-xsd-file-relationships.md) e cole-o para substituir o código que foi adicionado para o novo arquivo XSD por padrão.  
  
4.  Clique em qualquer lugar no Editor de XML e selecione **Designer de exibição**.  
  
5.  Selecione o modo de gráfico da barra de ferramentas XSD.  
  
6.  Selecione **esquema definido** nó no XML Schema Explorer e arraste o nó para criar suface do modo de exibição de gráfico. Você deve ver todos os nós globais, e as setas que conectam os nós que possuem relações.  
  
     ![Modo de exibição de gráfico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Clique em qualquer nó na superfície de design e examine a barra de rastreamento para ver onde o nó selecionado é localizado no conjunto de esquema.  
  
8.  Clique em qualquer nó de elemento em desing superfície e selecione **gerar XML de exemplo** para ver o documento de instância XML.