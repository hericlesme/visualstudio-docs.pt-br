---
title: 'DA0008: poucas amostras coletadas | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b4f472be09694e4e3bcfa0d3a60a2c1703534423
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="da0008-few-samples-collected"></a>DA0008: poucas amostras coletadas
|||  
|-|-|  
|ID de regra|DA0008|  
|Categoria|Uso das ferramentas de criação de perfil|  
|Método de criação de perfil|Amostragem|  
|Mensagem|Apenas algumas amostras foram coletadas. Considere uma execução mais longa ou uma taxa de amostragem mais rápida para obter resultados mais significativos.|  
|Tipo de regra|Informações|  
  
## <a name="cause"></a>Causa  
 Apenas algumas amostras foram coletadas na execução de criação de perfil.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando o método de amostragem é usado, é necessário coletar um número estatisticamente significativo de amostras para ter certeza de que os dados representam o comportamento real do programa. Para minimizar os erros de amostragem, é necessário tentar coletar, no mínimo, 1.000 amostras de comportamento de execução de instrução do programa. Se você não coletar amostras suficientes, poderá se confundir ao analisar os dados de criação de perfil.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Considere a criação de perfil de uma execução mais longa do aplicativo ou o uso de uma taxa de amostragem mais rápida para obter resultados estatisticamente significativos. Para obter informações sobre como alterar a taxa de amostragem na IDE do Visual Studio, consulte [Como escolher eventos de amostragem](../profiling/how-to-choose-sampling-events.md). Para obter mais informações sobre como alterar a taxa de amostragem ao usar a linha de comando das Ferramentas de Criação de Perfil, consulte [Timer](../profiling/timer.md) na referência [VSPerfCmd](../profiling/vsperfcmd.md).