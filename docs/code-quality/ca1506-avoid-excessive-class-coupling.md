---
title: 'CA1506: Evitar acoplamento de classes excessivo | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8192868aa7c5d79039a5e94a2aa13c47ada5d47c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: evitar acoplamento de classes excessivo
|||  
|-|-|  
|NomeDoTipo|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Categoria|Microsoft.Maintainability|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo ou método é associado a muitos outros tipos.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém.  
  
 Tipos e métodos que têm um alto grau de acoplamento de classes podem ser difíceis de manter. É uma boa prática têm tipos e métodos que exibem o acoplamento baixo e alta coesão.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir essa violação, tente recriar o tipo ou método para reduzir o número de tipos para o qual ele está ligado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Exclua este aviso quando o tipo ou método ainda é considerado sustentável apesar do grande número de dependências em outros tipos.  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)   
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)