---
title: 'CA2243: Literais de cadeia de caracteres de atributo devem ser analisados corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 79ffda960d85c05648a0f1ea7d6c759fc9e76f78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: os literais da cadeia de caracteres de atributo devem ser analisados corretamente
|||  
|-|-|  
|NomeDoTipo|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Parâmetro literal de cadeia de caracteres de um atributo não analisar corretamente para uma URL, o GUID ou a versão.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Como os atributos são derivados de <xref:System.Attribute?displayProperty=fullName>e os atributos são usados em tempo de compilação, somente valores constantes que podem ser passados para seus construtores. Parâmetros de atributo que devem representar URLs, GUIDs e versões não podem ser digitados como <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, e <xref:System.Version?displayProperty=fullName>, pois esses tipos não podem ser representados como constantes. Em vez disso, eles devem ser representados por cadeias de caracteres.  
  
 Como o parâmetro é digitado como uma cadeia de caracteres, é possível que um parâmetro formatado incorretamente pode ser passado em tempo de compilação.  
  
 Esta regra usa uma heurística de nomenclatura para localizar parâmetros que representam um uniform resource identifier (URI), um globalmente GUID (identificador exclusivo) ou uma versão e verifica se o valor passado está correto.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Altere a cadeia de caracteres do parâmetro para uma URL, o GUID ou o versão formado corretamente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o parâmetro não representam um URL, o GUID ou a versão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o código para o AssemblyFileVersionAttribute que violam essa regra.  
  
 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 A regra é disparada pelo seguinte:  
  
-   Parâmetros que contêm 'version' e não podem ser analisados para Version.  
  
-   Parâmetros que contêm 'guid' e não podem ser analisados como GUID.  
  
-   Parâmetros que contêm 'uri', 'urn' ou 'url' e não podem ser analisados para System. URI.  
  
## <a name="see-also"></a>Consulte também  
 [CA1054: os parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)