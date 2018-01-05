---
title: "CA1001: Tipos que possuem campos descartáveis devem ser descartáveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd2372acf82d275b0c240ee3fe1c17e687854340
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: tipos que tenham campos descartáveis devem ser descartáveis
|||  
|-|-|  
|NomeDoTipo|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não quebra - se o tipo não é visível fora do assembly.<br /><br /> Quebrar - se o tipo é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Uma classe declara e implementa um campo de instância é um <xref:System.IDisposable?displayProperty=fullName> tipo e a classe não implementa <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Uma classe que implementa o <xref:System.IDisposable> interface descarte de recursos não gerenciados que é proprietária. Um campo de instância é um <xref:System.IDisposable> tipo indica se o campo tem um recurso não gerenciado. Uma classe que declara um <xref:System.IDisposable> campo indiretamente possui um recurso não gerenciado e deve implementar o <xref:System.IDisposable> interface. Se a classe não possui todos os recursos não gerenciados diretamente, ele não deve implementar um finalizador.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, implementar <xref:System.IDisposable> e o <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chamada de método de <xref:System.IDisposable.Dispose%2A> método do campo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma classe que viola a regra e uma classe que satisfaz a regra ao implementar <xref:System.IDisposable>. A classe não implementa um finalizador porque a classe não possui todos os recursos não gerenciados diretamente.  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: tipos que tenham recursos nativos devem ser descartáveis](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)