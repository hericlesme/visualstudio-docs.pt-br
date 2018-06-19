---
title: Designer de fluxo de trabalho - Designer de atividade de FinalState
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d89e9f81bb7dc8237069a79784eadc0e5d375d6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972531"
---
# <a name="finalstate-activity-designer"></a>Designer de atividade de FinalState

O designer de <xref:System.Activities.Core.Presentation.FinalState> é usado para criar <xref:System.Activities.Statements.State> que termina uma instância do computador de estado.

## <a name="using-the-finalstate-activity-designer"></a>Usando o designer de atividade de FinalState

O **FinalState** designer é usado para criar um <xref:System.Activities.Statements.State> que é pré-configurado como um estado de terminação em uma máquina de estado. Um <xref:System.Activities.Statements.State> que é criado usando o <xref:System.Activities.Core.Presentation.FinalState> designer de atividade tem seu <xref:System.Activities.Statements.State.IsFinal%2A> propriedade definida como **true**, não tem nenhum <xref:System.Activities.Statements.State.Exit%2A> atividade e nenhuma transição proveniente dela. Para usar o <xref:System.Activities.Core.Presentation.FinalState> designer de atividade para adicionar um <xref:System.Activities.Statements.State> atividade que é pré-configurado como um estado de terminação em uma máquina de estado, arraste o **FinalState** designer de atividade do **máquina de estado**seção o **caixa de ferramentas** e solte-o para o designer de fluxo de trabalho. O designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> pode ser solto em <xref:System.Activities.Statements.StateMachine> e as transições adicionados posteriormente; ou uma transição pode ser criada como o designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> é descartada. Para obter mais informações sobre como criar transições, consulte [transição](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade do estado em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades que podem ser definidas usando o designer de <xref:System.Activities.Core.Presentation.FinalState> e descreve como elas são usadas no designer. Algumas dessas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.State> no cabeçalho. O valor padrão é **estado**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Statements.State.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Statements.State.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica a ação que ocorre quando esse estado é feito a transição para. Esse valor pode ser definido, arrastando uma atividade do **caixa de ferramentas** e descarte-a para o <xref:System.Activities.Statements.State.Entry%2A> seção do estado.|

## <a name="see-also"></a>Consulte também

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Estado](../workflow-designer/state-activity-designer.md)
- [transição](../workflow-designer/transition-activity-designer.md)