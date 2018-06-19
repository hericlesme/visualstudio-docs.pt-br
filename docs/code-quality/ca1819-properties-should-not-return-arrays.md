---
title: 'CA1819: as propriedades não devem retornar matrizes'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2aca450bba47b73c8fa2e5e8e1246e864a1293c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917725"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: as propriedades não devem retornar matrizes
|||
|-|-|
|NomeDoTipo|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma propriedade pública ou protegida em um tipo público retorna uma matriz.

## <a name="rule-description"></a>Descrição da Regra
 Matrizes retornadas pelas propriedades não são protegido contra gravação, mesmo se a propriedade é somente leitura. Para manter a matriz à prova de adulteração, a propriedade deve retornar uma cópia da matriz. Normalmente, os usuários não compreenderão as implicações adversas no desempenho de chamar uma propriedade assim. Especificamente, eles podem usar a propriedade como uma propriedade indexada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, verifique a propriedade de um método ou altere a propriedade para retornar uma coleção.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Atributos podem conter propriedades que retornam matrizes, mas não podem conter propriedades que retornam coleções. Você pode suprimir um aviso que é gerado para uma propriedade de um atributo que é derivado de <xref:System.Attribute> classe. Caso contrário, não suprima um aviso dessa regra.

## <a name="example-violation"></a>Violação de exemplo

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma propriedade que violam essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>Comentários
 Para corrigir uma violação desta regra, verifique a propriedade de um método ou altere a propriedade para retornar uma coleção em vez de uma matriz.

## <a name="change-the-property-to-a-method-example"></a>Altere a propriedade para um exemplo de método

### <a name="description"></a>Descrição
 O exemplo a seguir corrige a violação, alterando a propriedade a um método.

### <a name="code"></a>Código
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>Retorna um coleção de exemplo

### <a name="description"></a>Descrição
 O exemplo a seguir corrige a violação, alterando a propriedade para retornar um

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>Permitir que os usuários modificar uma propriedade

### <a name="description"></a>Descrição
 Você talvez queira permitir que o consumidor da classe modificar uma propriedade. O exemplo a seguir mostra uma propriedade de leitura/gravação que violam essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>Comentários
 O exemplo a seguir corrige a violação, alterando a propriedade para retornar um <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Código
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)