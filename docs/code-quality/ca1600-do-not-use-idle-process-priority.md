---
title: 'CA1600: não usar a prioridade de processo ociosa'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d052d2e6d9e3b47217cc6ce25fe752e0e2859437
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: não usar a prioridade de processo ociosa
|||
|-|-|
|NomeDoTipo|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Categoria|Microsoft.Mobility|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Essa regra ocorre quando os processos são definidos como `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Descrição da Regra
 Não defina a prioridade do processo como Ocioso. Processos que têm `System.Diagnostics.ProcessPriorityClass.Idle` ocuparão a CPU quando ele não esteja ocioso e, portanto, bloquearão standby.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Definir processos `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Essa regra deve ser suprimida somente quando a prioridade de processo ociosa é necessária e considerações de mobilidade podem ser ignoradas com segurança.