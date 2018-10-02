---
title: 'CA2216: Os tipos descartáveis devem declarar finalizador | Microsoft Docs'
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
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7e44ead74e7bcedefff69fefd2ebaf7a478faa3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587260"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: os tipos descartáveis devem declarar o finalizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2216: os tipos descartáveis devem declarar o finalizador](https://docs.microsoft.com/visualstudio/code-quality/ca2216-disposable-types-should-declare-finalizer).

|||
|-|-|
|NomeDoTipo|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName>e tem campos que sugerem o uso de recursos não gerenciados, não implementa um finalizador, conforme descrito pelo <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Uma violação dessa regra será relatada se o tipo descartável contém campos dos tipos a seguir:

-   <xref:System.IntPtr?displayProperty=fullName>

-   <xref:System.UIntPtr?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, implemente um finalizador que chama sua <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se o tipo não implementa <xref:System.IDisposable> com a finalidade de liberar recursos não gerenciados.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2115: chamar GC.KeepAlive durante o uso de recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: tipos que tenham recursos nativos devem ser descartáveis](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Consulte também
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Padrão de descarte](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



