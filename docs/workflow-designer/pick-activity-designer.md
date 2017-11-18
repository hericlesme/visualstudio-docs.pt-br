---
title: Escolha o Designer de atividade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: "9"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa06d4c63dbb18c080c8a6b8ffda01838607ba55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="pick-activity-designer"></a>Escolha o designer de atividades
A atividade de <xref:System.Activities.Statements.Pick> fornece o fluxo de controle baseado. A atividade executa um dos vários ramificações em resposta a um evento disparando.  
  
## <a name="the-pick-activity"></a>A atividade de picareta  
 Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de objetos <xref:System.Activities.Statements.PickBranch> , uma que a atividade de <xref:System.Activities.Statements.Pick> pode executar devido a qualquer evento de entrada que serve como um disparador. Dessa forma [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornece a modelagem com base em eventos de fluxo de controle. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>. No início de um <xref:System.Activities.Statements.Pick> a execução da atividade, todas as atividades de gatilho de <xref:System.Activities.Statements.PickBranch> elementos estão agendados. Quando a primeira atividade concluir, a atividade correspondente de ação está agendada, e quaisquer atividades restantes do disparador serão canceladas.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta  
 O **escolher** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **escolher** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que os designers de atividade normalmente são colocados, por exemplo, dentro de um  **Sequência** designer de atividade. Após solto na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], cria uma atividade de <xref:System.Activities.Statements.Pick> , que contém por padrão duas atividades vazios de <xref:System.Activities.Statements.PickBranch> como elementos com nomes para exibição de Branch1 e de Branch2. Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no **PickBranch** cabeçalho de designer de atividade ou dentro de **propriedades** janela para cada ramificação.  
  
 Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> atividades para a coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastando e soltando o **PickBranch** designer do **caixa de ferramentas** ou usando o menu de contexto dentro de **escolher** superfície de design. Para obter detalhes, consulte o [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tópico. Observe que o único item que pode ser colocado dentro de um **escolher** designer de atividade é uma **PickBranch** designer de atividade.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Escolha propriedades de atividade em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Pick> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Pick> no cabeçalho. O valor padrão é picareta. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de controle](../workflow-designer/control-flow-activity-designers.md)   
 [Escolher atividade](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Usando a atividade de picareta](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)