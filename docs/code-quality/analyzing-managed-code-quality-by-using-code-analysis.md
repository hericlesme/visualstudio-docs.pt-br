---
title: "Analisando a qualidade do código gerenciado usando a análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 2008ac649302d87cc2d45274de3fdb1981aa571d
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2018
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analisando a qualidade do código gerenciado usando a análise de código
Você pode usar as ferramentas de análise de código no Visual Studio para descobrir problemas potenciais no seu código, como acesso a dados não seguras, violações de uso e problemas de design. Análise de código funciona no .NET Framework, nativo (C e C++) e aplicativos de banco de dados. Análise de código para código gerenciado organiza regras *conjuntos de regras* destino específico de problemas de codificação.  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefas comuns|Conteúdo de suporte|  
|------------------|------------------------|  
|**Adquira prática:** Conheça os fundamentos da análise de código por corrigir defeitos em um aplicativo simple do .NET Framework.|-   [Passo a passo: Analisando código gerenciado em busca de defeitos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurar a análise de código para um projeto:** regras gerenciado código são organizadas em conjuntos de regras que se destinam a áreas específicas, como design e de segurança. Você pode usar um dos Microsoft regra padrão define ou criar seus próprios.|-   [Análise de código para visão geral de código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Suprimir Avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Executar análise de código:** você pode especificar a análise de código para ser executada automaticamente toda vez que uma configuração de projeto é criada, e você pode executar a análise de código manualmente em um projeto.|-   [Como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Como: executar a análise de código manualmente](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analisar resultados de análise de código:** erros e avisos de análise de código são listados na janela análise de código. Você pode escolher um título de erro ou um aviso para exibir informações adicionais sobre o aviso e para exibir e realce a linha de código fonte que disparou a regra. Você pode escolher a id de aviso para exibir informações detalhadas na biblioteca do MSDN que inclui informações e exemplos sobre como resolver o problema.|-   [Como: Exibir defeitos de código gerenciado](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Análise de código para avisos de código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avisos por CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Métodos anônimos e análise de código](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrar a análise de código com o seu ciclo de vida de desenvolvimento:** políticas de Check-in no [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] habilitar as equipes de desenvolvimento para certificar-se de que todos os check-ins de código atendem a um conjunto comum de padrões de análise de código. Criar um item de trabalho para uma violação de regra de análise de código é um procedimento simples que você pode executar na janela lista de erros.|-   [Melhorando a qualidade do código com políticas de Check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Como: sincronizar conjuntos de regras do projeto de código com política de Check-in do projeto de equipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Como: criar um Item de trabalho para um defeito de código gerenciado](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|