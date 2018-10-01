---
title: Classificação, filtragem e agrupamento (XML Schema Explorer) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9cb8086e894130fa20f8c270c9dafe6b302c989c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472661"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Classificação, filtragem e agrupamento (XML Schema Explorer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [classificação, filtragem e agrupamento (XML Schema Explorer)](https://docs.microsoft.com/visualstudio/xml-tools/sorting-filtering-and-grouping-xml-schema-explorer).  
  
  
Este tópico descreve as opções que estão disponíveis por meio de **opções de agrupamento, filtragem e classificação** menu na barra de ferramentas XML Schema Explorer.  
  
## <a name="filter-options"></a>Opções de filtro  
 As seguintes opções de filtro estão disponíveis. Por padrão, o **Mostrar Namespaces** e **Mostrar arquivos do esquema** opções são selecionadas.  
  
-   **Exibir Namespaces**.  
  
-   **Exibir arquivos de esquema**.  
  
-   **Exibir compositores (sequência/escolha/tudo)**.  
  
## <a name="sorting-options"></a>Opções de classificação  
 As seguintes opções de classificação estão disponíveis. O padrão é **classificar por tipo**. O tipo por opções não se aplica a arquivos e para namespaces.  
  
-   **Classificar por tipo**.  
  
-   **Classificar por nome**.  
  
-   **Ordem do documento**.  
  
### <a name="sort-by-type"></a>Classificar por Tipo  
 Quando o **classificar por tipo** opção estiver selecionada, os nós globais são classificados na seguinte ordem. Nós são classificados em ordem alfabética dentro de cada grupo.  
  
1.  nós de`import` .  
  
2.  nós de`include` .  
  
3.  nós de`redefine` .  
  
4.  nós de`attribute` .  
  
5.  nós de`attributeGroup` .  
  
6.  nós de`complexType` .  
  
7.  nós de`simpleType` .  
  
8.  nós de`element` .  
  
9. nós de`group` .  
  
### <a name="sort-by-name"></a>Classificar por Nome  
 Quando o **classificar por nome** opção estiver selecionada, os nós globais são classificados na seguinte ordem:  
  
1.  nós de`import` (em ordem alfabética namespaces).  
  
2.  nós de`include` (em ordem alfabética de atributos de `schemaLocation` ).  
  
3.  nós de`redefine` (em ordem alfabética de atributos de `schemaLocation` ).  
  
4.  Outros nós globais em ordem alfabética.  
  
### <a name="document-order"></a>Ordem de documento  
 O **ordem do documento** opção está disponível quando o **Mostrar arquivos do esquema** opção está selecionada. Quando **ordem do documento** for selecionada, os nós globais são exibidos na ordem em que aparecem no arquivo de esquema.  
  
## <a name="persisting-sortfilter-options"></a>Gravando o tipo/opções de filtro  
 A classificação, filtragem, e opções de agrupamento são salvas no Registro para cada usuário, não importa qual a solução ou arquivos estavam aberta quando as configurações foram alteradas.





