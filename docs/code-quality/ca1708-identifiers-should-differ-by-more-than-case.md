---
title: "CA1708: Os identificadores devem ser diferentes de maiusculas de minúsculas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda7936a1a701b1b51957a7038db496f70ddd9c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Os nomes dos dois tipos, membros, parâmetros ou espaços para nome totalmente qualificados são idênticos quando eles são convertidos em minúsculas.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. Por exemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] é uma linguagem de maiusculas e minúsculas amplamente usada.  
  
 Esta regra é disparada em membros publicamente visíveis apenas.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Selecione um nome exclusivo quando comparado a outros identificadores em minúsculas.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Não pode ser utilizada em todos os idiomas disponíveis na biblioteca de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="example-of-a-violation"></a>Exemplo de uma violação  
 O exemplo a seguir demonstra uma violação desta regra.  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)