---
title: Desenvolvendo aplicativos com o Designer de fluxo de trabalho | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 61d58b172c185a908a6314664ccd4cfe2172dc8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desenvolvendo aplicativos com designers de Fluxo de Trabalho
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] é um designer e um depurador visuais para a compilação e gráficos a depuração de aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] que está hospedada no ambiente de desenvolvimento de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] . Permite que você escreve um aplicativo de fluxo de trabalho, uma biblioteca de atividade, ou um serviço composto de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] com o uso de modelos e os designers de atividade. [!INCLUDE[crabout](../test/includes/crabout_md.md)]fluxos de trabalho, consulte o [Windows Workflow Foundation &#91;. .NET Framework 4 &#93; ](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
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
  
## <a name="in-this-section"></a>Nesta seção  
 [Usando o Designer de Fluxo de Trabalho](../workflow-designer/using-the-workflow-designer.md)  
 Mostra como criar novos atividades e fluxo de trabalho usando os projetos designer internos e como usar outras ferramentas fornecidas pelo designer para argumentos, a variáveis, para expressões, as importações, e a navegação de trilha de manipular.  
  
 [Usando os designers de atividade](../workflow-designer/using-the-activity-designers.md)  
 Descreve as categorias de atividades e modelos e seus designers que são sistema fornecidos.  
  
 [Fluxos de trabalho de depuração com o Designer de Fluxo de Trabalho](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Descreve como executar procedimentos de depuração bem como a depuração XAML e expressões tradicionais.  
  
 [Ajuda da interface do usuário do Designer de Fluxo de Trabalho](../workflow-designer/workflow-designer-ui-help.md)  
 Contém tópicos da ajuda contextual para as caixas de diálogo fornecidas por [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], bem como orientação sobre recursos, em atalhos de teclado e de mensagens de erro do shell de designer.  
  
 [Desenvolvendo aplicativos de fluxo de trabalho destinados ao .NET 3.0 ou o .NET Framework 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contém a orientação sobre como usar o designer herdado que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Designer ReHosting &#91; Exemplos de WF &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 Este exemplo mostra como criar o layout de WPF para conter o designer.  
  
 [Designers de atividade personalizada](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 Esta seção contém exemplos de atividade que usam designer personalizadas para exibição no designer de fluxo de trabalho.