---
title: Designer de fluxo de trabalho - exibições de atividade (legados)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d3453ecefece93f593c3d4ebbc261e4332815da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="activity-views-legacy"></a>Visualizações de atividade (legados)

Muitas das atividades fornecidas do Windows Workflow Foundation (WF), do qual os fluxos de trabalho são compostos por tem várias exibições de design disponíveis no Designer de fluxo de trabalho herdado do Windows. Quando você arrasta um designer de atividade do **caixa de ferramentas** na superfície de design e, assim, sempre que você selecionar a atividade, você pode alternar entre os modos de exibição de design diferentes, usando o **defluxodetrabalho**menu ou clicando com a atividade selecionada. Além disso, quando você move o ponteiro sobre o nome de uma atividade selecionada, um conjunto lista suspensa de guias que aparece você pode usar para alternar entre modos de exibição diferentes.

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

- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)
- [Exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md)