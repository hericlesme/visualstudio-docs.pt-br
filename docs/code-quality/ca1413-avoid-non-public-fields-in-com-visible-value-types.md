---
title: 'CA1413: evitar campos não públicos em tipos de valor visíveis COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11f2badbf6af73367dcdfe90344012704b8de8b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917075"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: evitar campos não públicos em tipos de valor visíveis COM
|||
|-|-|
|NomeDoTipo|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo de valor que está marcado como visível para COM Component Object Model () especificamente declara um campo de instância não público.

## <a name="rule-description"></a>Descrição da Regra
 Os campos de instância não pública dos tipos de valor visíveis por COM permanecem visíveis para clientes COM. Revise o conteúdo do campo para informações que não devem ser expostos ou que terá um efeito não intencional de design ou de segurança.

 Por padrão, todos os tipos de valor público estão visíveis para COM. No entanto, para reduzir o número de falsos positivos, essa regra requer a visibilidade de COM do tipo a ser declarado explicitamente. O assembly contendo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definida como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra e manter o campo ocultado, altere o tipo de valor para um tipo de referência ou remova o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se exposição pública do campo for aceitável.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1407: evitar membros estáticos em tipos visíveis em COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index) [qualificando tipos do .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)