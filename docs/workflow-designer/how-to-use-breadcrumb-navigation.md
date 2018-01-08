---
title: "Como: Use a navegação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 95e79ab384c6311aa17f2592b514d62b899b8b6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-breadcrumb-navigation"></a>Como: Use a navegação de rastreamento
Existem três maneiras principais de alterar o conjunto de atividades que são exibidas em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]:  
  
1.  Clique duas vezes para furar na uma atividade filho.  
  
2.  Clique em um botão na barra de rastreamento para navegar em uma atividade de ancestral.  
  
3.  Expandir ou recolher atividades no lugar.  
  
### <a name="using-breadcrumb-navigation"></a>Usando a navegação de rastreamento  
  
1.  Clique duas vezes em uma atividade de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] para alterar a atividade raiz a atividade clicado. A atividade clicada completa é expandida na raiz e seus ancestrais são mostrados na barra de rastreamento. Isso é às vezes chamado perfuração ou de uma atividade.  
  
2.  Para navegar a um predecessor de atividade atual da raiz, clique na atividade na barra de rastreamento.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Expandindo ou recolhendo uma atividade no lugar  
  
1.  Clique nas vigas em uma atividade expande ou recolhe a atividade no lugar.  
  
2.  Quando o estado do estado de expansão é alterado clicando no botão, o novo estado de expansão é salvo em XAML.  
  
    > [!WARNING]
    >  Nem todas as atividades podem ser expandidos no lugar. Há dois casos quando uma atividade não pode ser expandida no local: ou o pai da atividade não permite seus filhos sejam expandidos no lugar, (por exemplo, as atividades em um fluxograma não podem ser expandidos no local), ou o designer de atividade não se permite que é expandido no lugar. Embora nenhum dos designers atividade estão incluídos em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] tenham o último comportamento, quaisquer atividades personalizados podem exibir esse comportamento.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Tudo expandir ou recolher todas as atividades  
  
1.  Use o **Expandir tudo** e **Recolher tudo** botões na interface do usuário para expandir ou recolher todas as atividades sob a raiz da trilha de navegação atual. Observe que expande todas e recolhe todo é estados globais. Isso significa que quando você alterar a atividade raiz usando a navegação de trilha, expandir todos ou recolhe todos os estados persiste até que você clique **restauração**.  
  
2.  Depois que você aplicou um Expandir tudo ou recolhe todos os estados, você pode clicar no **restaurar** botão que aparece para voltar para examinar o estado anteriormente aplicado a cada atividade.  
  
    > [!WARNING]
    >  Se uma atividade, como <xref:System.Activities.Statements.Flowchart>, tenha optado de expandir em vigor, a funcionalidade associado a **Expandir tudo** e **Recolher tudo** botões está desabilitado no **fluxograma**  designer. [!INCLUDE[crabout](../test/includes/crabout_md.md)]o **fluxograma** designer, consulte o [fluxograma](../workflow-designer/flowchart-activity-designer.md) tópico.  
  
    > [!WARNING]
    >  Expandir tudo também tem um efeito especial **Switch** e **TryCatch** designers de atividade. Quando você clica em **Expandir tudo**, todos os casos de comutador e todos os blocos try/catch/finally são exibidos. Clicando em **restaurar** ou **Recolher tudo** retorna esses designers para seu estado padrão, que você pode clicar em um caso/bloco individual para exibir seu conteúdo.