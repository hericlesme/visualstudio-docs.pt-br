---
title: 'CA1307: Especificar StringComparison | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7087cfe23f7911ec33891a70cd88cf47ee9e4a7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: especificar StringComparison
|||  
|-|-|  
|NomeDoTipo|SpecifyStringComparison|  
|CheckId|CA1307|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define uma <xref:System.StringComparison> parâmetro.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Muitas operações, mais importantes de cadeia de caracteres de <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A> métodos, forneça uma sobrecarga que aceita um <xref:System.StringComparison> valor de enumeração como um parâmetro.  
  
 Sempre que existir de uma sobrecarga que utiliza um <xref:System.StringComparison> parâmetro, ele deve ser usado em vez de uma sobrecarga que não têm esse parâmetro. Definindo explicitamente esse parâmetro, seu código é geralmente feita mais clara e mais fáceis de manter.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere os métodos de comparação de cadeia de caracteres para sobrecargas que aceitam o <xref:System.StringComparison> enumeração como um parâmetro. Por exemplo: alterar `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo é destinado a um público limitado de local e, portanto, não será localizado.  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de globalização](../code-quality/globalization-warnings.md)   
 [CA1309: usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)