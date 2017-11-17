---
title: "Escolhendo um modelo de solução de linguagem específica do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Escolhendo um modelo de solução de linguagem específica do domínio
Para criar uma solução de linguagem específica de domínio, escolha um dos modelos de solução que estão disponíveis no Assistente do Designer de linguagem específica de domínio. Escolhendo o modelo que mais se assemelha a linguagem que você deseja criar, você pode minimizar as modificações que você precisa fazer para a solução inicial.  
  
 Os modelos de solução a seguir estão disponíveis no Assistente de Designer de linguagem específica de domínio.  
  
|Modelo|Recursos|Descrição|  
|--------------|--------------|-----------------|  
|Diagramas de classe|-Formas compartimento<br />-Herança de classe<br />-Herança de relacionamento<br />-Forma de herança<br />-Propriedades de relação|Use esse modelo de solução se sua linguagem específica de domínio inclui entidades e relações que têm propriedades. Este modelo cria uma linguagem específica de domínio que se parece com diagramas de classe UML. As principais entidades são classes e interfaces, junto com as relações de associação, generalização e implementação. Uma classe ou interface aparece como uma caixa que contém uma lista de atributos.|  
|Diagramas de componente|-Portas|Use esse modelo de solução se sua linguagem específica de domínio inclui componentes, ou seja, partes de um sistema de software. Este modelo cria uma linguagem específica de domínio que se parece com diagramas de componente UML. As principais entidades são componentes e portas, que aparecem como formas pequenas fora dos componentes.|  
|Diagramas de fluxo de tarefas|-Imagens e formas de geometria<br />-   *Raias*|Use esse modelo de solução se sua linguagem específica de domínio inclui sequências, estados ou fluxos de trabalho. Este modelo cria uma linguagem específica de domínio que se parece com diagramas de atividade UML. A entidade principal é uma atividade e a relação principal é uma transição entre atividades. O modelo inclui vários outros elementos, como o estado inicial, o estado final e uma barra de sincronização.|  
|Idioma mínimo|-Uma classe e forma<br />-Uma relação e conector|Use esse modelo de solução se sua linguagem específica de domínio não for parecido com os outros modelos. Este modelo cria uma linguagem específica de domínio que tem duas classes e uma relação, que são representados no **caixa de ferramentas** como **caixa** e **linha**. A classe e a relação tem uma propriedade de cadeia de caracteres de exemplo.|  
|Designer do WinForm mínima|-Um modelo pequeno.<br />-Um formulário do Windows que exibe o modelo.|Use este modelo para criar um aplicativo no qual uma DSL está associada a um formulário do Windows, em vez de um designer gráfico.<br /><br /> O formulário que atua como a interface do usuário para o idioma está na pasta Dsl\UI.<br /><br /> Você deve compilar o projeto antes de abrir o designer de formulário.<br /><br /> Para obter mais informações, consulte [criando uma linguagem específica de domínio de Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Mínimo de WPF Designer|-Um modelo pequeno<br />-Uma interface de usuário do Windows Presentation Foundation que exibe o modelo|Use este modelo para criar um aplicativo no qual uma DSL está associada a uma interface de usuário do WPF, em vez de um designer gráfico.<br /><br /> O designer para a interface do usuário está na pasta Dsl\UI.<br /><br /> Você deve compilar o projeto antes de abrir o designer de interface do usuário.<br /><br /> Para obter mais informações, consulte [criando uma linguagem específica de domínio de WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Biblioteca DSL|-Uma biblioteca mínima|Use este modelo para criar uma definição parcial de DSL que pode ser importada para outras definições de DSL.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das Ferramentas de Linguagem Específica de Domínio](../modeling/overview-of-domain-specific-language-tools.md)
