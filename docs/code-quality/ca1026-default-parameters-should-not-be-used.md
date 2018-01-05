---
title: "CA1026: Parâmetros padrão não devem ser usados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43f83bf88e017da06ee3653019aa91807229d55e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: parâmetros padrão não devem ser usados
|||  
|-|-|  
|NomeDoTipo|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo visível externamente contém um método externamente visível que usa um parâmetro padrão.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os métodos que usam parâmetros padrão são permitidos no Common Language Specification (CLS); No entanto, o CLS permite que os compiladores ignorar os valores que são atribuídos a esses parâmetros. Código que está escrito para compiladores que ignoram valores de parâmetro padrão explicitamente deve fornecer argumentos para cada parâmetro padrão. Para manter o comportamento que você deseja em linguagens de programação, os métodos que usam parâmetros padrão devem ser substituídos com sobrecargas do método que fornecem os parâmetros padrão.  
  
 O compilador ignora os valores de parâmetros padrão para extensão gerenciadas para C++ quando ele acessa o código gerenciado. O compilador do Visual Basic oferece suporte a métodos que têm parâmetros padrão que usam o [opcional](/dotnet/visual-basic/language-reference/modifiers/optional) palavra-chave.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua o método que usa os parâmetros padrão com as sobrecargas do método que fornecem os parâmetros padrão.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que usa os parâmetros padrão e os métodos sobrecarregados que fornecem uma funcionalidade equivalente.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1025: substituir argumentos repetitivos por matriz de parâmetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>Consulte também  
 [Componentes de independência de linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)