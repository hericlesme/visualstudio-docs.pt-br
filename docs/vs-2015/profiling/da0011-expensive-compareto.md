---
title: 'DA0011: CompareTo dispendioso | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9958e9ec729591aa89c97d4f1d23a819e7b7eeb6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475660"
---
# <a name="da0011-expensive-compareto"></a>DA0011: função CompareTo dispendiosa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente do Visual Studio 2017, consulte [DA0011: CompareTo dispendiosa](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) em docs.microsoft.com.  
  
|||  
|-|-|  
|ID de regra|DA0011|  
|Categoria|Uso do .NET Framework|  
|Métodos de criação de perfil|Amostragem<br /><br /> Memória do .NET|  
|Mensagem|As funções de CompareTo devem ser baratas e podem não alocar nenhuma memória. Reduza a complexidade da função CompareTo se possível.|  
|Tipo de regra|Aviso|  
  
## <a name="cause"></a>Causa  
 O método CompareTo de tipo é dispendioso ou aloca memória.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os métodos do CompareTo devem ser eficientes e não devem alocar memória.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Reduza a complexidade do método CompareTo.

