---
title: "Exibições de atividade (legados) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 50f57684db32f601bd4cbf870456da458aa5ce7c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="activity-views-legacy"></a>Visualizações de atividade (legados)
Muitas das atividades fornecidas por [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], que fluxos de trabalho são compostos, têm várias exibições de design disponíveis em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado. Quando você arrasta um designer de atividade do **caixa de ferramentas** na superfície de design e, assim, sempre que você selecionar a atividade, você pode alternar entre os modos de exibição de design diferentes, usando o **defluxodetrabalho**menu ou clicando com a atividade selecionada. Além disso, quando você move o ponteiro sobre o nome de uma atividade selecionada, um conjunto lista suspensa de guias que aparece você pode usar para alternar entre modos de exibição diferentes.  
  
 Cada atividade tem pelo menos uma exibição; Esta é a exibição padrão mostrada quando você arrasta um designer de atividade do **caixa de ferramentas** na superfície de design. Este modo de exibição de padrão de atividade está disponível como a **exibir [tipo de atividade]** opção nos menus e na guia, por exemplo, **exibição paralelo**. A maioria das atividades têm modos de exibição adicionais e as atividades diferentes podem ter diferentes modos de exibição. Por exemplo, o [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) atividade tem o modo de exibição e o [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) atividade tem eventos de um modo de exibição. Muitas das atividades que vêm com o Windows Workflow Foundation têm **Exibir Cancelar manipulador** e **falhas de exibição** criar modos de exibição para exibir o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e um [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associados a eles.  
  
 A tabela a seguir lista o nome e a descrição de cada uma.  
  
|Opção de menu/guia|Descrição|  
|----------------------|-----------------|  
|**Exibição [tipo de atividade]**|Selecione este menu catalogue ou a opção para exibir a representação gráfica padrão de atividade selecionada.|  
|**Exibir manipulador de cancelamento**|Selecione esta opção de menu ou na guia exibição o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associada à atividade selecionada.|  
|**Controle de falhas de modo de exibição**|Selecione esta opção de menu ou na guia exibição o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associada à atividade selecionada.|  
|**Exibir manipulador de compensação**|Selecione esta opção de menu ou na guia exibição o [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associado selecionado [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Manipulador de eventos de exibição**|Selecione esta opção de menu ou na guia exibição o [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) selecionado associado a [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Para obter informações sobre modos de exibição semelhantes, consulte [exibições sequenciais de fluxo de trabalho (legados)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atividades de fluxo de trabalho herdados](../workflow-designer/legacy-workflow-activities.md)   
 [Exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md)