---
title: 'CA1051: não declarar campos de instância visíveis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc08d39e842afa8bee9baa89f4c788f291d90ea2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899092"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: não declarar campos de instância visíveis
|||
|-|-|
|NomeDoTipo|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo visível externamente tem um campo de instância visíveis externamente.

## <a name="rule-description"></a>Descrição da Regra
 O principal uso de um campo deve ser um como um detalhe da implementação. Campos devem ser `private` ou `internal` e devem ser expostos por meio de propriedades. É fácil de acessar uma propriedade que é para acesso a um campo e o código nos acessadores de uma propriedade pode alterar como os recursos do tipo expanda sem introduzir alterações significativas. Propriedades que retornam apenas o valor de um campo particular ou interno são otimizadas para executar no acesso a um campo. ganho de desempenho muito pouco está associado com o uso de campos visíveis externamente sobre as propriedades.

 Refere-se visível externamente para `public`, `protected`, e `protected internal` (`Public`, `Protected`, e `Protected Friend` no Visual Basic) níveis de acessibilidade.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, verifique o campo `private` ou `internal` e expô-lo usando uma propriedade visível externamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Campos visíveis externamente não fornecem nenhum benefício que não está disponível para propriedades. Além disso, os campos públicos não podem ser protegidos por [demandas de Link](/dotnet/framework/misc/link-demands). Consulte [CA2112: tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo (`BadPublicInstanceFields`) que violam essa regra. `GoodPublicInstanceFields` mostra o código corrigido.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Consulte também
 [Demandas de link](/dotnet/framework/misc/link-demands)