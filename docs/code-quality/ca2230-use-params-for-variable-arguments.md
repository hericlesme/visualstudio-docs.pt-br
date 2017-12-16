---
title: "CA2230: Usar parâmetros para argumentos variáveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d578a68cfa5ff6b29d3e625dfd00b76e9994240a
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: usar parâmetros para argumentos variáveis
|||  
|-|-|  
|NomeDoTipo|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou protegido contém um método público ou protegido que usa o `VarArgs` convenção de chamada.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O `VarArgs` convenção de chamada é usada com determinadas definições de método que levam a um número variável de parâmetros. Um método usando o `VarArgs` convenção de chamada não é Common Language Specification (CLS) compatível e pode não estar acessível em linguagens de programação.  
  
 No c#, o `VarArgs` convenção de chamada é usada quando a lista de parâmetros do método termina com a `__arglist` palavra-chave. Visual Basic não dá suporte a `VarArgs` chamando convenção e Visual C++ permite o uso apenas em código não gerenciado que usa a elipse `...` notação.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra em c#, use o [params](/dotnet/csharp/language-reference/keywords/params) palavra-chave em vez de `__arglist`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois métodos, um que viola a regra e um que atenda a regra.  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Componentes de independência de linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)