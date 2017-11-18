---
title: "CA2130: As constantes críticas de segurança devem ser transparentes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9975acd53976b1668e158fd3e906c669a0f5ed49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: as constantes críticas de segurança devem ser transparentes
|||  
|-|-|  
|NomeDoTipo|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um campo constante ou um membro de enumeração é marcado com o <xref:System.Security.SecurityCriticalAttribute>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 A imposição de transparência não é imposta para valores constantes porque compiladores têm valores constantes internos de modo que nenhuma pesquisa seja necessária no tempo de execução. Os campos constantes devem ter segurança transparente de forma que os revisores de código não pressuponham que o código transparente não pode acessar a constante.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo SecurityCritical do campo ou valor.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 Nos exemplos a seguir, o valor de enum `EnumWithCriticalValues.CriticalEnumValue` e a constante `CriticalConstant` gerar esse aviso. Para corrigir os problemas, remova o [`SecurityCritical`] atributo para torná-los segurança transparente.  
  
 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]