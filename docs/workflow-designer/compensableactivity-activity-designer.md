---
title: Designer de fluxo de trabalho - Designer de atividade de CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdab42766fd20989831e446a45115d17b3ee28fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="compensableactivity-activity-designer"></a>Designer de atividade de CompensableActivity

O **CompensableActivity** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.CompensableActivity> atividade.

## <a name="the-compensableactivity-activity"></a>A atividade de CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> define uma unidade de trabalho que pode ser compensado confirmada ou após a conclusão com êxito.

### <a name="using-the-compensableactivity-activity-designer"></a>Usando o designer de atividade de CompensableActivity
 O **CompensableActivity** designer de atividade pode ser encontrado no **transação** categoria de **caixa de ferramentas**. Para abrir **caixa de ferramentas**, selecione o **caixa de ferramentas** guia no lado esquerdo do Designer de fluxo de trabalho. Como alternativa, selecione **barra de ferramentas** do **exibição** menu ou pressione CTRL + ALT + X.

 O **CompensableActivity** designer de atividades pode ser arrastado **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho. Você pode arrastar o designer de atividade dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o designer de atividade cria um <xref:System.Activities.Statements.CompensableActivity> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de CompensableActivity. Editar o <xref:System.Activities.Activity.DisplayName%2A> valor no cabeçalho do **CompensableActivity** designer de atividade. Ele também pode ser editado no **DisplayName** caixa da grade de propriedade.

### <a name="the-compensableactivity-properties"></a>As propriedades de CompensableActivity
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CompensableActivity> e descreve como elas são usadas no designer. O <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> propriedade pode ser editada na grade de propriedade, mas as outras propriedades devem ser editadas na superfície do Designer de fluxo de trabalho.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CompensableActivity> . O padrão é CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Especifica o valor de retorno de <xref:System.Activities.Statements.CompensableActivity>. Esta propriedade deve ser editada na grade de propriedade.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|verdadeiro|Especifica a atividade para que a compensação, cancelamento, e a lógica de confirmação são fornecidos. Para adicionar o <xref:System.Activities.Statements.CompensableActivity.Body%2A> atividade, soltar uma atividade de **caixa de ferramentas** no **corpo** caixa o **CompensableActivity** designer de atividade. Adicione o texto da dica "Descartar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Especifica a atividade que é executada quando há um cancelamento. Para adicionar a atividade, descartar seu designer de **caixa de ferramentas** para o **CancellationHandler** caixa o **CompensableActivity** designer de atividade. Adicione texto de dica "Descartar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Especifica a atividade a ser executada para compensar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Compensate> .<br /><br /> Para adicionar a atividade, descartar seu designer de atividade de **caixa de ferramentas** para o **CompensationHandler** caixa o **CompensableActivity** designer de atividade. Adicione texto de dica "Descartar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Especifica a atividade a ser executada para confirmar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Confirm> .<br /><br /> Para adicionar a atividade, descartar seu designer de atividade de **caixa de ferramentas** para o **ConfirmationHandler** caixa o **CompensableActivity** designer de atividade. Adicione texto de dica "Descartar atividade aqui".|

## <a name="see-also"></a>Consulte também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)