---
title: 'CA2215: Métodos Dispose devem chamar o descarte da classe base | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bacd16fa8c58fcbe6646e1b7c5f2a26fad8e4ce3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586995"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: os métodos de descarte devem chamar o descarte da classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2215: métodos Dispose devem chamar o descarte da classe base](https://docs.microsoft.com/visualstudio/code-quality/ca2215-dispose-methods-should-call-base-class-dispose).

|||
|-|-|
|NomeDoTipo|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> herda de um tipo que também implementa <xref:System.IDisposable>. O <xref:System.IDisposable.Dispose%2A> método do tipo de herança não chama o <xref:System.IDisposable.Dispose%2A> método do tipo pai.

## <a name="rule-description"></a>Descrição da Regra
 Se um tipo herda de um tipo descartável, ele deve chamar o <xref:System.IDisposable.Dispose%2A> método do tipo base de dentro de seu próprio <xref:System.IDisposable.Dispose%2A> método. Chamar o método de tipo base Dispose garante que todos os recursos criados pelo tipo de base são liberados.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chame `base`.<xref:System.IDisposable.Dispose%2A> no seu <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se a chamada para `base`.<xref:System.IDisposable.Dispose%2A> ocorre em um nível mais profundo de chamada que as verificações de regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeB` que herda do tipo `TypeA` e chama corretamente sua <xref:System.IDisposable.Dispose%2A> método.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.IDisposable?displayProperty=fullName> [Padrão de descarte](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



