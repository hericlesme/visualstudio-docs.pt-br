---
title: 'CA1046: Não sobrecarregar operador equals em tipos de referência | Microsoft Docs'
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
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1f4f37f6d4c2662ca0b053e6737c57ba222b0b5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587031"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: não sobrecarregar igualdades de operador em tipos de referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1046: não sobrecarregar operador equals em tipos de referência](https://docs.microsoft.com/visualstudio/code-quality/ca1046-do-not-overload-operator-equals-on-reference-types).

|||
|-|-|
|NomeDoTipo|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo de referência pública ou público aninhado sobrecarrega o operador de igualdade.

## <a name="rule-description"></a>Descrição da Regra
 Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta. Por padrão, duas referências só serão iguais se apontarem para o mesmo objeto.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova a implementação do operador de igualdade.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, quando o tipo de referência se comporta como um tipo de valor interno. Se for significativo para fazer a adição ou subtração em instâncias do tipo, é provavelmente correto implementar o operador de igualdade e suprimir a violação.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o comportamento padrão ao comparar duas referências.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir compara algumas referências.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **um = novo (2,2) e b = novo (2,2) são iguais? Não**
**c e a são igual? Sim**
**b e a são = =? Não**
**c e a são = =? Sim**
## <a name="related-rules"></a>Regras relacionadas
 [CA1013: sobrecarregar operador Equals ao sobrecarregar adicionar e subtrair](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Operadores de igualdade](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



