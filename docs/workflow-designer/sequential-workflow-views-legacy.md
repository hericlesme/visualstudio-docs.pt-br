---
title: "Modos de exibição do fluxo de trabalho sequencial (herdado) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 74aac4ab6406b4f400d6d5951c00b2a92af91ec0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="sequential-workflow-views-legacy"></a>Exibições sequenciais de fluxo de trabalho (legados)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] fornece [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] herdado que pode ser usado para direcionar [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornece uma maneira de criar aplicativos graficamente de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando a interface do usuário e de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . aplicativos de[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] são compostos das etapas do processo de fluxo de trabalho chamadas atividades. Para criar um fluxo de trabalho, compor as atividades na superfície de design arrastando seus designers de atividade do respectivos de **caixa de ferramentas** na superfície de design.  
  
 Quando você cria um fluxo de trabalho sequencial, o que é um [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), três modos de exibição do fluxo de trabalho estão disponíveis. Essas exibições são acessíveis a partir de **fluxo de trabalho** menu e no menu de contexto na superfície de design.  
  
 A tabela a seguir lista o nome e a descrição de cada uma.  
  
|Opção de menu/guia|Descrição|  
|----------------------|-----------------|  
|**Modo de exibição SequentialWorkflow**|Clique a superfície de design e selecione o **exibição SequentialWorkflow** opção no menu de contexto para exibir o **fluxo de trabalho sequencial** exibição, que mostra a atividade com base em gráfica representação do fluxo de trabalho sequencial. Ou selecione **exibição SequentialWorkflow** do **fluxo de trabalho** menu.|  
|**Exibir manipulador de cancelamento**|Clique a superfície de design e selecione o **Exibir Cancelar manipulador** opção no menu de contexto para exibir o **fluxo de trabalho sequencial** exibir, que mostra o [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) atividade associada com o fluxo de trabalho. Ou selecione **Exibir Cancelar manipulador** do **fluxo de trabalho** menu.|  
|**Controle de falhas de modo de exibição**|Clique a superfície de design e selecione o **manipulador de falhas de modo de exibição** opção no menu de contexto para exibir o **falhas** exibir, que mostra o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) atividade associada com o fluxo de trabalho. Ou selecione **manipulador de falhas de modo de exibição** do **fluxo de trabalho** menu.|  
  
 Para obter mais informações sobre modos de exibição semelhantes, consulte [exibições de atividade (legados)](../workflow-designer/activity-views-legacy.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de atividade (legados)](../workflow-designer/activity-views-legacy.md)   
 [Criando projetos de fluxo de trabalho herdado](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modos de criação de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65014)