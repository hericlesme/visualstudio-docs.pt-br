---
title: 'CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c952d4cf2533034c12a287149404bee6d267214
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
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