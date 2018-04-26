---
title: Designer de fluxo de trabalho - modos de exibição do fluxo de trabalho sequencial (legados)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce1217ea629ae0301b72b444161d61db4fe448b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="sequential-workflow-views-legacy"></a>Exibições sequenciais de fluxo de trabalho (legados)

Visual Studio 2010 fornece um Designer de fluxo de trabalho herdado do Windows que podem ser usados para direcionar o .NET Framework versão 3.5 ou o WinFX.

O Designer de fluxo de trabalho fornece uma maneira de criar graficamente os aplicativos do Windows Workflow Foundation (WF) usando a interface de usuário familiar do Visual Studio. Aplicativos do Windows Workflow Foundation (WF) são compostos de etapas do processo de fluxo de trabalho chamadas atividades. Para criar um fluxo de trabalho, compor as atividades na superfície de design arrastando seus designers de atividade do respectivos de **caixa de ferramentas** na superfície de design.

Quando você cria um fluxo de trabalho sequencial, o que é um [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), três modos de exibição do fluxo de trabalho estão disponíveis. Essas exibições são acessíveis a partir de **fluxo de trabalho** menu e no menu de contexto na superfície de design.

A tabela a seguir lista o nome e a descrição de cada uma.

|Opção de menu/guia|Descrição|
|----------------------|-----------------|
|**Modo de exibição SequentialWorkflow**|Clique a superfície de design e selecione o **exibição SequentialWorkflow** opção no menu de contexto para exibir o **fluxo de trabalho sequencial** exibição, que mostra a atividade com base em gráfica representação do fluxo de trabalho sequencial. Ou selecione **exibição SequentialWorkflow** do **fluxo de trabalho** menu.|
|**Exibir manipulador de cancelamento**|Clique a superfície de design e selecione o **Exibir Cancelar manipulador** opção no menu de contexto para exibir o **fluxo de trabalho sequencial** exibir, que mostra o [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) atividade associada com o fluxo de trabalho. Ou selecione **Exibir Cancelar manipulador** do **fluxo de trabalho** menu.|
|**Controle de falhas de modo de exibição**|Clique a superfície de design e selecione o **manipulador de falhas de modo de exibição** opção no menu de contexto para exibir o **falhas** exibir, que mostra o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) atividade associada com o fluxo de trabalho. Ou selecione **manipulador de falhas de modo de exibição** do **fluxo de trabalho** menu.|

 Para obter mais informações sobre modos de exibição semelhantes, consulte [exibições de atividade (legados)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Consulte também

- [Exibições de atividade (herdado)](../workflow-designer/activity-views-legacy.md)
- [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)
- [Modos de criação de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65014)