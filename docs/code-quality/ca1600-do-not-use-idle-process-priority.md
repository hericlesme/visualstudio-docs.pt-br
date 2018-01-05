---
title: "CA1600: Não use prioridade de processo ociosa | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d1646cd587295f2854399cfc24603ce1f1910e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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