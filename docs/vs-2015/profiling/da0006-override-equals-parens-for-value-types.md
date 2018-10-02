---
title: 'DA0006: substituir Equals() para tipos de valor | Microsoft Docs'
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
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4e7535775946c99d6b176f36ca10288a8bc9da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466678"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: substituir Equals() para tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [DA0006: substituir Equals () para tipos de valor](https://docs.microsoft.com/visualstudio/profiling/da0006-override-equals-parens-for-value-types).  
  
Id da regra | DA0006 |  
| Categoria de |. Uso do .NET Framework |  
| Métodos de criação de perfil | Amostragem |  
| Mensagem | Substituir Equals e operador de igualdade em tipos de valor. |  
| Tipo de mensagens | Aviso |  
  
## <a name="cause"></a>Causa  
 Chamadas para o método Equals ou os operadores de igualdade de um tipo de valor público são uma parte significativa dos dados de criação de perfil. Considere a implementação de um método mais eficiente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Para tipos de valor, a implementação herdada de Equals usa a biblioteca <xref:System.Reflection> e compara o conteúdo de todos os campos do tipo. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias ou as usem como chaves de tabela de hash, o tipo de valor deverá implementar Equals. Se a linguagem de programação der suporte à sobrecarga de operador, também é necessário fornecer uma implementação dos operadores de igualdade e desigualdade.  
  
 Para obter mais informações sobre como substituir Equals e os operadores de igualdade, consulte [Diretrizes para Implementação de Equals e o Operador de Igualdade (= =)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Como investigar um aviso  
 Para obter um exemplo de implementação de Equals e operadores de igualdade, consulte a regra de análise de código [CA1815: substituir Equals e operador Equals em tipos de valor](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)



