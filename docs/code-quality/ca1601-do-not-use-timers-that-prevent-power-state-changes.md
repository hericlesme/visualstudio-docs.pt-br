---
title: 'CA1601: Não usar temporizadores que impeçam alterações no estado de energia | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 270c030d4d4b829fb1e7d17308a4ae6f0ad17539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: não usar temporizadores que impeçam alterações no estado de energia
|||  
|-|-|  
|NomeDoTipo|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Categoria|Microsoft.Mobility|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um temporizador tem um intervalo definido para ocorrer mais de uma vez por segundo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Não pesquise com mais frequência do que uma vez por segundo ou use timers que ocorrem com mais frequência do que uma vez por segundo. A atividade periódica de alta frequência manterá a CPU ocupada e interferirá nos temporizadores ociosos que economizam energia e desligam monitores e discos rígidos.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Definir intervalos de timer para ocorrem menos de uma vez por segundo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Essa regra deve ser suprimida somente se o timer de acionamento mais de uma vez por segundo é necessário e considerações de mobilidade podem ser ignoradas.