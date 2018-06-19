---
title: 'CA2213: os campos descartáveis devem ser descartados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be4efbd197a8146789b9646f6b5c467cc42815b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920479"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: os campos descartáveis devem ser descartados
|||
|-|-|
|NomeDoTipo|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara os campos que são de tipos que implementam também <xref:System.IDisposable>. O <xref:System.IDisposable.Dispose%2A> método do campo não é chamado pelo <xref:System.IDisposable.Dispose%2A> método do tipo declarativo.

## <a name="rule-description"></a>Descrição da Regra
 Um tipo é responsável por descartar todos os seus recursos não gerenciados; Isso é realizado pela implementação <xref:System.IDisposable>. Esta regra verifica se um tipo descartável `T` declara um campo `F` que é uma instância de um tipo descartável `FT`. Para cada campo `F`, a regra tenta localizar uma chamada para `FT.Dispose`. A regra pesquisará os métodos chamados pelo `T.Dispose`e um nível inferior (os métodos chamados pelos métodos chamados pelo `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, chame <xref:System.IDisposable.Dispose%2A> em campos que são de tipos que implementam <xref:System.IDisposable> se você é responsável por alocar e liberar os recursos não gerenciados mantido pelo campo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se você não é responsável por liberar os recursos mantidos por campo, ou se a chamada para <xref:System.IDisposable.Dispose%2A> ocorre em um nível mais profundo de chamada que as verificações de regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable> (`FT` na discussão previosu).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeB` que violam essa regra declarando um campo `aFieldOfADisposableType` (`F` na discussão anterior) como um tipo descartável (`TypeA`) e não chamar <xref:System.IDisposable.Dispose%2A> no campo. `TypeB` corresponde à `T` na discussão anterior.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.IDisposable?displayProperty=fullName> [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)