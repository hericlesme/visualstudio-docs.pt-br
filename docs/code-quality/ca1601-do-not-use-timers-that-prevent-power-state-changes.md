---
title: "CA1601: Não usar temporizadores que impeçam alterações no estado de energia | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5fc42c15beda68472f4a980fe96b0055b70a01cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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