---
title: 'CA1309: Usar StringComparison ordinal | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cf913eea3f156595c9b9194b3d8a74e71b848367
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: usar StringComparison ordinal
|||  
|-|-|  
|NomeDoTipo|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Uma operação de comparação de cadeia de caracteres que é nonlinguistic não define o <xref:System.StringComparison> parâmetro a **Ordinal** ou **OrdinalIgnoreCase**.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Muitas operações, mais importantes de cadeia de caracteres de <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName> métodos, agora fornecem uma sobrecarga que aceita um <xref:System.StringComparison?displayProperty=fullName> valor de enumeração como um parâmetro.  
  
 Quando você especificar um **StringComparison** ou **OrdinalIgnoreCase**, a comparação de cadeia de caracteres será nonlinguistic. Ou seja, os recursos que são específicos para o idioma natural são ignorados ao tomar decisões de comparação. Isso significa que as decisões se baseiam em comparações de byte simples e Ignorar maiusculas e minúsculas ou equivalência de tabelas que são parametrizadas pela cultura. Como resultado, definindo explicitamente o parâmetro como o **StringComparison** ou **OrdinalIgnoreCase**, seu código geralmente ganhar velocidade, aumenta a exatidão e torna-se mais confiável.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o método de comparação de cadeia de caracteres para uma sobrecarga que aceita o <xref:System.StringComparison?displayProperty=fullName> enumeração como um parâmetro e especifique o **Ordinal** ou **OrdinalIgnoreCase**. Por exemplo, altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo é destinado para um público local limitado ou quando a semântica da cultura atual deve ser usada.  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de globalização](../code-quality/globalization-warnings.md)   
 [CA1307: especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)