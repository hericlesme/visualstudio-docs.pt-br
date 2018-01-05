---
title: "CA1505: Evitar código insatisfatória | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5abaaba67d3390e36c4ad792d7b95bf41be80c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: evitar código que não possa ser mantido
|||  
|-|-|  
|NomeDoTipo|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|Categoria|Microsoft.Maintainability|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O índice de facilidade de manutenção é calculado usando as seguintes métricas: linhas de código, o volume de programa e complexidade ciclomática igual. Volume do programa é uma medida da dificuldade de compreensão de um tipo ou método que é baseado no número de operadores e operandos no código. A complexidade ciclomática é uma medida da complexidade estrutural do tipo ou método. Você pode aprender mais sobre as métricas de código em [medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Um índice de facilidade de manutenção baixa indica que um tipo ou método é provavelmente difíceis de manter e seria uma boa candidata para reprojetar.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir essa violação, recriar o tipo ou método e tente dividi-lo em tipos menores e mais direcionados ou métodos.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Exclua este aviso quando um tipo ou método ainda é considerado sustentável apesar de tamanho grande ou quando o tipo ou método não pode ser dividido.  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)   
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)