---
title: Designer de atividade WriteLine | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 615cfb46222dfbf6e6b3cb1ba6741cde7c7bf708
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="writeline-activity-designer"></a>Designer de atividade WriteLine
O **WriteLine** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.WriteLine> atividade.  
  
## <a name="the-writeline-activity"></a>A atividade WriteLine  
 Grava de atividade de <xref:System.Activities.Statements.WriteLine> texto a <xref:System.IO.TextWriter> um objeto especificado. Se nenhum <xref:System.IO.TextWriter> é especificado, <xref:System.Activities.Statements.WriteLine> grava o texto no console.  
  
### <a name="using-the-writeline-activity-designer"></a>Usando o designer de atividade WriteLine  
 O **WriteLine** designer de atividade pode ser encontrado no **primitivos** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O **WriteLine** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.WriteLine> com <xref:System.Activities.Activity.DisplayName%2A> padrão WriteLine. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **WriteLine** designer de atividade ou o **DisplayName** caixa da grade de propriedade.  
  
### <a name="the-writeline-properties"></a>As propriedades WriteLine  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.WriteLine> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.WriteLine> . O padrão é WriteLine. Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é prática recomendada usar esse.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|O texto a gravação. Para definir a propriedade, digite uma expressão do Visual Basic no **texto** caixa o **WriteLine** atividade designer ou na grade de propriedades.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> a <xref:System.Activities.Statements.WriteLine> que grava <xref:System.Activities.Statements.WriteLine.Text%2A>. O padrão é o console.|  
  
## <a name="see-also"></a>Consulte também  
 [Primitivos](../workflow-designer/primitives-activity-designers.md)   
 [Atribuir](../workflow-designer/assign-activity-designer.md)   
 [Atraso](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)