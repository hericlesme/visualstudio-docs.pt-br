---
title: 'CA1026: parâmetros padrão não devem ser usados'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 173a9a62ea6a3106c50fd18f37180b583e0bb42c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
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