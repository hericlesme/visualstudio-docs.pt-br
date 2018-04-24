---
title: Conjuntos de regras de análise de código no Visual Studio
ms.date: 04/02/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a445aecdd5a9f02bca8d43e42646c991742a626
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Conjuntos de regras de uso para agrupar regras de análise de código

Quando você configura a análise de código no Visual Studio, você pode escolher de uma lista de interno *conjuntos de regras*. Um conjunto de regras se aplicam a um projeto e é um agrupamento de código de regras de análise para identificam problemas de destino e as condições específicas para o projeto. Por exemplo, você pode aplicar um conjunto de regras que foi projetado para verificar o código de APIs disponível publicamente, ou apenas o mínimo recomendado regras. Você também pode aplicar um conjunto de regras que inclui todas as regras.

Você pode personalizar uma conjunto de regras, adicionando ou excluindo regras ou alterando severidades de regra para aparecem como avisos ou erros no **lista de erros**. Conjuntos de regras personalizado podem atender uma necessidade de seu ambiente de desenvolvimento específico. Quando você personaliza um conjunto de regras, o editor de conjunto de regras fornece pesquisa e ferramentas para ajudá-lo no processo de filtragem.

## <a name="rule-set-format"></a>Formato do conjunto de regras

Um conjunto de regras é especificado em formato XML em um *. RuleSet* arquivo. Regras, que consistem em uma ID e um *ação*, são agrupadas por ID de analisador e o namespace no arquivo.

O conteúdo XML de um *. RuleSet* arquivo é semelhante a este:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> É mais fácil [editar um conjunto de regras](../code-quality/working-in-the-code-analysis-rule-set-editor.md) no gráfico **Editor de conjunto de regra** que manualmente.

A regra definida para um projeto é especificado o `CodeAnalysisRuleSet` propriedade no arquivo de projeto do Visual Studio. Por exemplo:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Consulte também

- [Referência do conjunto de regras de análise de código](../code-quality/rule-set-reference.md)
