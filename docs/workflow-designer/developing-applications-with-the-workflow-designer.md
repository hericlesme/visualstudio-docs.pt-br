---
title: Desenvolvendo aplicativos com o Designer de fluxo de trabalho | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 75a6fb6eef1f5e8e174607ac141646ab237dd285
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desenvolvendo aplicativos com designers de Fluxo de Trabalho

O Designer de fluxo de trabalho do Windows é um designer visual e o depurador para a construção de gráfica e a depuração de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos o [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] que está hospedado no [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ambiente de desenvolvimento. Permite que você escreve um aplicativo de fluxo de trabalho, uma biblioteca de atividade, ou um serviço composto de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] com o uso de modelos e os designers de atividade. Para obter mais informações sobre fluxos de trabalho, consulte o [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Os seguintes são vários novos recursos de design esse conjunto essa nova versão de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] independentemente das versões anteriores de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] é compilado usando [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Isso melhora a experiência do designer de atividade e melhora o desempenho para grandes e fluxos de trabalho complexos.

-   As atividades personalizados são criadas agora com [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], usando XAML e o modelo de programação para criar designer de atividade foi simplificado.

-   Uma atividade do fluxograma era implementado, então você pode visualizar o fluxo de programa usando o fluxograma familiar que modela o estilo.

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] tem um novo designer variável que permite que você declare e defina o escopo variáveis em seus fluxos de trabalho, associando os às atividades.

-   Em [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornece recursos do IntelliSense para criar expressões do Visual Basic dentro dos fluxos de trabalho [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] .

-   A experiência de depuração estende agora em XAML, permitindo que você defina pontos de interrupção na definição de fluxo de trabalho XAML e entrar no seu código XAML em tempo de execução, que fornece uma experiência semelhante ao código gerenciado.

-   Rehosting [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fora de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simplificado extremamente em comparação com versões anteriores, que requer agora apenas algumas linhas de código.

-   O novo <xref:System.Activities.Statements.Flowchart> atividade e seu [fluxograma](../workflow-designer/flowchart-activity-designer.md) permitem que você visualize seu fluxo de programa usando o fluxograma familiar estilo de modelagem.

-   As atividades de mensagem foram aprimoradas, permitindo que você escreva (nenhum código declarativo completa) serviços de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] .

-   O **adicionar referência de serviço...**  funcionalidade permite que você gere atividades automaticamente que acessar serviços da Web.