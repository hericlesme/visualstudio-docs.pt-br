---
title: 'DA0004: alto uso de processador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5800acfded9d500c68a0e071ffa6501d6b3c77e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749604"
---
# <a name="da0004-high-processor-usage"></a>DA0004: uso do processador elevado
|||  
|-|-|  
|ID de regra|DA0004|  
|Categoria|Uso das ferramentas de criação de perfil|  
|Métodos de criação de perfil|Instrumentação<br /><br /> Amostragem|  
|Mensagem|O uso do processador é consistentemente superior a 75%. Considere o uso do modo de Amostragem para aplicativos associados à CPU.|  
|Tipo de regra|Informações|  
  
 Ao criar o perfil usando a amostragem, a memória do .NET ou métodos de contenção de recursos, é necessário coletar pelo menos 10 amostras para disparar essa regra.  
  
## <a name="cause"></a>Causa  
 A utilização do processador (CPU) estava alta em dados de criação de perfil que foram coletados usando o método de instrumentação. Considere o uso do método de criação de perfil de amostragem ao criar o perfil de um aplicativo associado à CPU.  
  
## <a name="rule-description"></a>Descrição da regra  
 Durante essa execução de criação de perfil, o processador (ou os processadores) estava consistentemente ocupado. A alta utilização da CPU pode indicar um aplicativo associado à CPU. Perfis instrumentados não são a maneira mais eficiente de investigar cenários de uso da CPU. A amostragem é mais eficaz quando você está criando o perfil de aplicativos que gastam muito tempo para executar instruções no processador.  
  
## <a name="how-to-fix-violations"></a>Como corrigir violações  
 Considere uma nova criação de perfil do aplicativo usando o método de amostragem em vez do método de instrumentação, a menos que você precise de tempos de função ou esteja mais interessado em entender a entrada/saída do que os gargalos do processador.