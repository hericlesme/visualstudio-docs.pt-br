---
title: "DA0010: função GetHashCode dispendiosa | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ff2dbc1d98375b7199ab710412639fe4333c342d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: função GetHashCode dispendiosa
|||  
|-|-|  
|ID de regra|DA0010|  
|Categoria|Uso do .NET Framework|  
|Métodos de criação de perfil|Amostragem<br /><br /> Memória do .NET|  
|Mensagem|As funções de GetHashCode devem ser baratas e não podem alocar nenhuma memória. Se for possível, reduza a complexidade da função de código de hash.|  
|Tipo de mensagem|Aviso|  
  
## <a name="cause"></a>Causa  
 As chamadas para o método GetHashCode do tipo são uma parte significativa dos dados de criação de perfil ou do método de alocação de memória.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O hash é uma técnica para localizar rapidamente um item específico em uma coleção grande. As tabelas de hash podem ser enormes e dão suporte às altas taxas de acesso e, por isso, são muito eficientes. No entanto, uma implicação desse requisito é que os métodos GetHashCode no .NET Framework não devem alocar memória. A alocação de memória aumenta a carga no coletor de lixo e expõe o método para possíveis atrasos se for necessário executar de uma coleta de lixo como um resultado da solicitação de alocação.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Reduza a complexidade do método.