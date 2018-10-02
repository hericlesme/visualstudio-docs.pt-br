---
title: 'CA1601: Não usar temporizadores que impeçam alterações no estado de energia | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: de1b5e943274b80d8a46d05dcd0cdb8fe8b2b82a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586977"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: não usar temporizadores que impeçam alterações no estado de energia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1601: não usar temporizadores que impeçam alterações no estado de energia](https://docs.microsoft.com/visualstudio/code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes).

|||
|-|-|
|NomeDoTipo|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Categoria|Microsoft.Mobility|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um temporizador tem um intervalo definido para ocorrer mais de uma vez por segundo.

## <a name="rule-description"></a>Descrição da Regra
 Não faça sondagens com mais frequência do que uma vez por segundo ou use timers que ocorrem com mais frequência do que uma vez por segundo. A atividade periódica de alta frequência manterá a CPU ocupada e interferirá nos temporizadores ociosos que economizam energia e desligam monitores e discos rígidos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Definir intervalos de timer para ocorrer a menos de uma vez por segundo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Essa regra deve ser suprimida somente se o temporizador de acionamento mais de uma vez por segundo é necessária e considerações de mobilidade podem ser ignoradas com segurança.



