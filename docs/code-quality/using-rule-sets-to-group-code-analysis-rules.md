---
title: "Usando conjuntos de regras para agrupar regras de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 265ca57904cb47c52ecaf6ba260e726da9b8a063
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2018
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Usando conjuntos de regras para agrupar regras de análise de código

Quando você configura a análise de código no Visual Studio, você pode escolher de uma lista de internos da Microsoft *conjuntos de regras*. Um conjunto de regras é um agrupamento lógico de regras de análise de código que identificam problemas de destino e as condições específicas. Por exemplo, você pode aplicar um conjunto de regras que foi projetado para verificar o código de APIs disponível publicamente, ou você pode aplicar um conjunto de regras que inclui apenas o mínimo recomendado de regras. Você também pode aplicar um conjunto de regras que inclui todas as regras.

Você pode personalizar uma regra definida, adicionando ou excluindo regras ou alterando regras no **lista de erros** janela como avisos ou erros. Conjuntos de regras personalizado podem atender uma necessidade de seu ambiente de desenvolvimento específico. Quando você personaliza um conjunto de regras, a página de conjunto de regra fornece pesquisa e ferramentas para ajudá-lo no processo de filtragem.

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Adquira prática:** Use as ferramentas de análise de código para especificar uma regra personalizada definida para encontrar e corrigir problemas em um aplicativo simple do .NET Framework.|- [Passo a passo: Configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Configurar a análise de código para um projeto:** escolher uma regra existente definida para um projeto, o site da Web ou a solução.|- [Como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />- [Usando conjuntos de regras para especificar as regras do C++ para executar](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />- [Como: configurar a análise de código para um aplicativo Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />- [Como: especificar conjuntos de regras para vários projetos em uma solução](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Personalizar um conjunto de regras:** especificar regras para aplicar ao seu projeto.|- [Criando conjuntos de regras personalizado](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Entender os conjuntos de regras internas:** exibir as regras de análise de código que compõem os conjuntos de regras internas.|- [Referência de conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md)|
|**Integrar a análise de código com o Team Foundation Server:** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] check-in políticas permitem que as equipes de desenvolvimento certificar-se de que todos os check-ins código atender a um conjunto comum de padrões de análise de código.|- [Como: sincronizar conjuntos de regras do projeto de código com política de Check-in do projeto de equipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|