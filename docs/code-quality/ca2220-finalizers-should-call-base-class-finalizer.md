---
title: 'CA2220: Os finalizadores devem chamar o finalizador da classe base | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa5ed3329d4168a0781243a4faf021de3488e77c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: os finalizadores devem chamar o finalizador da classe base
|||  
|-|-|  
|NomeDoTipo|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo que substitui <xref:System.Object.Finalize%2A?displayProperty=fullName> não chama o <xref:System.Object.Finalize%2A> método na sua classe base.  
  
## <a name="rule-description"></a>Descrição da Regra  
 A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, tipos devem chamar a classe base <xref:System.Object.Finalize%2A> método de dentro de seus próprios <xref:System.Object.Finalize%2A> método. O compilador c# adiciona automaticamente a chamada para o finalizador da classe base.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame o tipo base <xref:System.Object.Finalize%2A> método de sua <xref:System.Object.Finalize%2A> método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Alguns compiladores que se destinam a common language runtime inserir uma chamada para o finalizador do tipo base em Microsoft intermediate language (MSIL). Se um aviso dessa regra for relatado, o compilador não insere a chamada, e você deve adicioná-lo ao seu código.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo do Visual Basic mostra um tipo `TypeB` que chama corretamente o <xref:System.Object.Finalize%2A> método na sua classe base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)