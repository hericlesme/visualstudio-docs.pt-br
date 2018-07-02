---
title: 'DA0011: CompareTo dispendioso | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d23ec25909dbce150600674136117183758f5fb
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750409"
---
# <a name="da0011-expensive-compareto"></a>DA0011: função CompareTo dispendiosa
|||  
|-|-|  
|ID de regra|DA0011|  
|Categoria|Uso do .NET Framework|  
|Métodos de criação de perfil|Amostragem<br /><br /> Memória do .NET|  
|Mensagem|As funções de CompareTo devem ser baratas e podem não alocar nenhuma memória. Reduza a complexidade da função CompareTo se possível.|  
|Tipo de regra|Aviso|  
  
## <a name="cause"></a>Causa  
 O método CompareTo de tipo é dispendioso ou aloca memória.  
  
## <a name="rule-description"></a>Descrição da regra  
 Os métodos do CompareTo devem ser eficientes e não devem alocar memória.  
  
## <a name="how-to-fix-violations"></a>Como corrigir violações  
 Reduza a complexidade do método CompareTo.