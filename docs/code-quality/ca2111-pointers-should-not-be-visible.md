---
title: 'CA2111: os ponteiros não devem estar visíveis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b7688910275414f1421fe81dffc5bc3efcd1d93
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916368"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: os ponteiros não devem estar visíveis
|||
|-|-|
|NomeDoTipo|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um público ou protegido <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> campo não é somente leitura.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.IntPtr> e <xref:System.UIntPtr> são tipos de ponteiro que são usados para acessar a memória não gerenciada. Se não houver um ponteiro privada, interna ou somente leitura, um código mal-intencionado pode alterar o valor do ponteiro, potencialmente, permitindo o acesso aos locais arbitrários na memória ou causando falhas de aplicativo ou sistema.

 Se você pretende proteger o acesso para o tipo que contém o campo de ponteiro, consulte [CA2112: tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Proteger o ponteiro, tornando-o somente leitura, interna ou privada.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso de que essa regra se você não confiar no valor do ponteiro.

## <a name="example"></a>Exemplo
 O código a seguir mostra os ponteiros que violam e atendem à regra. Observe que os ponteiros não privados também violam a regra [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Consulte também
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>