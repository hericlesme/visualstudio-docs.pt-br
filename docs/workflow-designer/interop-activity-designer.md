---
title: Designer de atividade de interoperabilidade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3adc99e0a09d2d82049dcbe816f14b24ab48a55d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="interop-activity-designer"></a>Designer de atividade de Interoperabilidade
O **Interop** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Interop> atividade.  
  
## <a name="the-interop-activity"></a>A atividade de Interoperabilidade  
 A atividade de <xref:System.Activities.Statements.Interop> gerencia a execução de tipos que derivam de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> em um fluxo de trabalho.  
  
### <a name="using-the-interop-activity-designer"></a>Usando o designer de atividade de Interoperabilidade  
 O **Interop** designer de atividade pode ser encontrado no **migração** categoria do **caixa de ferramentas**, que é acessado clicando o **ferramentas**guia (como alternativa, selecione **caixa de ferramentas** do **exibição** menu ou CTRL + ALT + X.)  
  
 O [migração](../workflow-designer/migration-activity-designers.md) categoria que contém o <xref:System.Activities.Statements.Interop> atividade aparece apenas no **caixa de ferramentas** se seu projeto se destina o completo [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Para projetos c#, você pode redirecionar o projeto para usar o completo [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] clicando com o projeto no **Solution Explorer** e selecionando **propriedades**. No **aplicativo** guia, selecione o **NET Framework 4** opção o **framework de destino**. Selecione o **Sim** no botão de **de alteração do Framework de destino** diálogo que é exibida solicitando que você confirmar esta alteração.  
  
 Para projetos VB, você pode direcionar novamente o projeto para usar o completo [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] clicando no projeto no **Solution Explorer** e selecionando **propriedades**. Sobre o **compilar** , clique no **opções avançadas de compilação** botão. Selecione **.Net Framework 4** do **lista do framework de destino** e, em seguida, clique em **Okey**. Clique no **Sim** no botão de **de alteração do Framework de destino** diálogo que é exibida solicitando que você confirmar esta alteração.  
  
 O **Interop** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.Interop> atividade com um padrão **DisplayName** de interoperabilidade. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **interoperabilidade** designer de atividade ou o **DisplayName** caixa da grade de propriedade.  
  
 Clique o **clique para procurar...**  texto no **ActivityType** caixa, no **Interop** atividade designer ou na grade de propriedades para exibir o **procurar e selecione um .net tipo** caixa de diálogo. Somente tipos para os trabalhos 3,0 ou o trabalho 3,5 atividades são mostrados (isto é, somente os tipos derivados de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../test/includes/crabout_md.md)]usando essa caixa para especificar um tipo, consulte o [procurar e selecione uma caixa de diálogo de tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tópico.  
  
### <a name="the-interop-properties"></a>As propriedades de Interoperabilidade  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Interop> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Interop> . O padrão é Interoperabilidade. Embora o nome para exibição não é necessário restrita, é uma prática recomendada usar um nome para exibição.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|verdadeiro|Especifica o tipo de atividade contida pela atividade de <xref:System.Activities.Statements.Interop> . Este tipo especificado deve derivar de <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Consulte também  
 [Migração](../workflow-designer/migration-activity-designers.md)