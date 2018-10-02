---
title: 'DA0013: alto uso de String.Split ou String.Substring | Microsoft Docs'
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
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8f835e120f730f9c223477959e9c93dfefa240
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473155"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: uso alto de String.Split ou String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [DA0013: alto uso de String. Split ou String. substring](https://docs.microsoft.com/visualstudio/profiling/da0013-high-usage-of-string-split-or-string-substring).  
  
Id da regra | DA0013 |  
| Categoria de |. Diretrizes de uso do .NET Framework |  
| Métodos de criação de perfil | Amostragem |  
| Mensagem | Considere reduzir o uso das funções String. Split e String. substring. |  
| Tipo de regra | Aviso |  
  
## <a name="cause"></a>Causa  
 Chamadas aos métodos System.String.Split ou System.String.Substring são uma proporção significativa dos dados de criação de perfil. Considere o uso de System.String.IndexOf ou System.String.IndexOfAny se estiver testando a existência de uma subcadeia de caracteres em uma cadeia de caracteres.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O método Split opera em um objeto String e retorna uma nova matriz de Strings que contém as subcadeias da original. A função aloca memória ao objeto de matriz retornado e aloca um novo objeto String a cada elemento de matriz encontrado. Da mesma forma, o método Substr opera em um objeto String e retorna uma nova String que é equivalente à subcadeia de caracteres solicitada.  
  
 Se o gerenciamento de alocações de memória for crítico para seu aplicativo, considere o uso de alternativas aos métodos String.Split e String.Substr. Por exemplo, é possível usar o método IndexOf ou IndexOfAny para localizar uma subcadeia de caracteres específica em uma cadeia de caracteres sem criar uma nova instância da classe String.  
  
## <a name="how-to-investigate-a-warning"></a>Como investigar um aviso  
 Clique duas vezes na mensagem da janela Lista de Erros para navegar para a [Exibição de Detalhes da Função](../profiling/function-details-view.md) dos dados de perfil de amostragem. Examine as funções de chamada para encontrar as seções do programa que fazem o uso mais frequente dos métodos System.String.Split ou System.String.Substr. Se possível, use o método IndexOf ou IndexOfAny para localizar uma subcadeia de caracteres específica em uma cadeia de caracteres sem criar uma nova instância da classe String.



