---
title: Modos de exibição de atividade (herdado) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ef7aaa042ea358ecdf3d45b6ee75dd14cf117a01
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466464"
---
# <a name="activity-views-legacy"></a>Visualizações de atividade (legados)
Muitas das atividades fornecidas por [!INCLUDE[wf](../includes/wf-md.md)], que fluxos de trabalho são compostos, têm várias exibições de design disponíveis em [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Quando você arrasta um designer de atividade do **caixa de ferramentas** na superfície de design e, assim, sempre que você selecione a atividade, você pode alternar entre os modos de exibição de design diferentes usando o **fluxo de trabalho**menus ou clicando-se a atividade selecionada. Além disso, quando você move o ponteiro sobre o nome de uma atividade selecionada, um conjunto lista suspensa de guias que aparece você pode usar para alternar entre modos de exibição diferentes.  
  
 Cada atividade tem pelo menos uma exibição; Esta é a exibição padrão exibida quando você arrasta um designer de atividade do **caixa de ferramentas** na superfície de design. Esta exibição de atividade está disponível como a **exibir [tipo de atividade]** opção na guia, por exemplo e menus **exibição paralela**. A maioria das atividades têm modos de exibição adicionais e as atividades diferentes podem ter diferentes modos de exibição. Por exemplo, o [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) atividade tem o modo de exibição e o [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) atividade tem eventos de um modo de exibição. Muitas das atividades que vêm com o Windows Workflow Foundation têm **exibir manipulador de cancelamento** e **View Faults** modos de exibição para o modo de exibição de design do [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e um [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associados a eles.  
  
 A tabela a seguir lista o nome e a descrição de cada uma.  
  
|Opção de menu/guia|Descrição|  
|----------------------|-----------------|  
|**Exibição [tipo de atividade]**|Selecione este menu catalogue ou a opção para exibir a representação gráfica padrão de atividade selecionada.|  
|**Exibir manipulador de cancelamento**|Selecione esta opção de menu ou catalogue modo de exibição para exibir o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associada à atividade selecionada.|  
|**Exibir manipulador de falha**|Selecione esta opção de menu ou catalogue modo de exibição para exibir o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associada à atividade selecionada.|  
|**Exibir manipulador de compensação**|Selecione esta opção de menu ou catalogue modo de exibição para exibir o [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associado com selecionado [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Exibir manipulador de eventos**|Selecione esta opção de menu ou catalogue modo de exibição para exibir o [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associado com selecionado a [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Para obter informações sobre modos semelhantes, consulte [exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atividades de fluxo de trabalho herdado](../workflow-designer/legacy-workflow-activities.md)   
 [Exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md)