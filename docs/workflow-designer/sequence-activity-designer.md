---
title: "Designer de atividade de sequência | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 5d0635839b9d875c5c519ec41c6dcfa6dc02fa2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sequence-activity-designer"></a>Arranje seqüencialmente o designer de atividades
A atividade de <xref:System.Activities.Statements.Sequence> contém uma coleção ordenada de atividades filhos que executa em ordem.  
  
 Outra maneira de executar um conjunto de atividades em ordem é usar uma atividade de <xref:System.Activities.Statements.Flowchart> . Considere o uso de [fluxograma](../workflow-designer/flowchart-activity-designer.md) quando você tiver uma ramificação simples ou fluxo de programa que você deseja modelar diagrammatically em loop.  
  
## <a name="using-the-sequence-activity-designer"></a>Usando o designer de atividade de sequência  
 Para adicionar um <xref:System.Activities.Statements.Sequence> atividade, arraste o **sequência** designer de atividade do **caixa de ferramentas** e solte-o para o [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] superfície. Para adicionar uma atividade filho a este <xref:System.Activities.Statements.Sequence> atividade, arraste algumas outras atividades do **caixa de ferramentas** e solte-o triângulo na caixa com o texto da dica "Descartar atividade aqui".  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade da sequência em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Sequence> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Sequence> no cabeçalho. O valor padrão é sequência. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
  
## <a name="see-also"></a>Consulte também  
 [Fluxograma](../workflow-designer/flowchart-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)