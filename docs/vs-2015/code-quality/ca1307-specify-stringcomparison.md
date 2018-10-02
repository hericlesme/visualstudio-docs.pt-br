---
title: 'CA1307: Especificar StringComparison | Microsoft Docs'
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
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2c96b8c895106337a8578b6662c0e61830b38f55
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587228"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: especificar StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1307: especificar StringComparison](https://docs.microsoft.com/visualstudio/code-quality/ca1307-specify-stringcomparison).

|||
|-|-|
|NomeDoTipo|SpecifyStringComparison|
|CheckId|CA1307|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método não define uma <xref:System.StringComparison> parâmetro.

## <a name="rule-description"></a>Descrição da Regra
 Muitas operações, mais importante da cadeia de caracteres a <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A> métodos, fornecer uma sobrecarga que aceita um <xref:System.StringComparison> valor de enumeração como um parâmetro.

 Sempre que uma sobrecarga existe que utiliza um <xref:System.StringComparison> parâmetro, ele deve ser usado em vez de uma sobrecarga que não utilize esse parâmetro. Definindo explicitamente esse parâmetro, seu código é geralmente feita mais clara e fácil de manter.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere métodos de comparação de cadeia de caracteres para sobrecargas que aceitam o <xref:System.StringComparison> enumeração como um parâmetro. Por exemplo: altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, quando a biblioteca ou o aplicativo é destinado a um público limitado de local e, portanto, não será localizado.

## <a name="see-also"></a>Consulte também
 [Avisos de globalização](../code-quality/globalization-warnings.md) [CA1309: usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)



