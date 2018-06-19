---
title: Desenvolvendo aplicativos com designers de Fluxo de Trabalho
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970119"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desenvolvendo aplicativos com designers de Fluxo de Trabalho

O Designer de fluxo de trabalho do Windows é um designer visual e o depurador para a construção de gráfica e a depuração de aplicativos do Windows Workflow Foundation (WF) no .NET Framework 4 que é hospedado no ambiente de desenvolvimento do Visual Studio 2010. Ele permite que compõem um aplicativo composto de fluxo de trabalho, a biblioteca de atividade ou o serviço do Windows Communication Foundation (WCF) com o uso de modelos e designers de atividade. Para obter mais informações sobre fluxos de trabalho, consulte o [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Estes são vários novos recursos de design que definir essa nova versão do Designer de fluxo de trabalho, além de versões mais antigas do Designer de fluxo de trabalho:

-   O Designer de fluxo de trabalho é criado usando o Windows Presentation Foundation (WPF). Isso melhora a experiência do designer de atividade e melhora o desempenho para grandes e fluxos de trabalho complexos.

-   As atividades personalizados são criadas agora com [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], usando XAML e o modelo de programação para criar designer de atividade foi simplificado.

-   Uma atividade do fluxograma era implementado, então você pode visualizar o fluxo de programa usando o fluxograma familiar que modela o estilo.

-   O Designer de fluxo de trabalho tem um novo variável designer que permite declarar e definir o escopo de variáveis em fluxos de trabalho, associá-los para atividades.

-   No Visual Studio 2010, o Designer de fluxo de trabalho fornece recursos completos do IntelliSense ao criar expressões do Visual Basic em seus fluxos de trabalho do .NET Framework 4.

-   A experiência de depuração estende agora em XAML, permitindo que você defina pontos de interrupção na definição de fluxo de trabalho XAML e entrar no seu código XAML em tempo de execução, que fornece uma experiência semelhante ao código gerenciado.

-   Nova hospedagem o Designer de fluxo de trabalho fora do Visual Studio seja bastante simplificado em comparação com versões anteriores, agora exigindo apenas algumas linhas de código.

-   O novo <xref:System.Activities.Statements.Flowchart> atividade e seu [fluxograma](../workflow-designer/flowchart-activity-designer.md) permitem que você visualize seu fluxo de programa usando o fluxograma familiar estilo de modelagem.

-   As atividades de mensagens foram aprimoradas, permitindo que você grave totalmente declarativa (sem código) serviços Windows Communication Foundation (WCF).

-   O **adicionar referência de serviço...**  funcionalidade permite que você gere atividades automaticamente que acessar serviços da Web.