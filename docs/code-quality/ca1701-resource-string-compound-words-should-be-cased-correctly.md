---
title: "CA1701: Palavras compostas de cadeia de caracteres de recurso devem ter maiusculas e minúsculas corretamente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dee5b21724944ea26e89c2cd1ace556f1377848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: as palavras compostas da cadeia de caracteres do recurso devem ter maiúsculas e minúsculas corretas
|||  
|-|-|  
|NomeDoTipo|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Uma cadeia de caracteres de recurso contém uma palavra composta que parece não ter maiusculas e minúsculas corretamente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Cada palavra na cadeia de caracteres de recurso é dividida em tokens com base em maiusculas e minúsculas. Cada combinação contígua de dois tokens é verificada pela biblioteca do verificador ortográfico da Microsoft. Se reconhecidas, as palavras produzirão uma violação da regra. São exemplos de palavras compostas que causam uma violação de "CheckSum" e "MultiPart", que deve ter maiusculas e minúsculas como "Checksum" e "Multipart", respectivamente. Devido ao uso comum anterior, várias exceções são incorporadas a regra e várias palavras únicas são sinalizadas como "Ferramentas" e "Filename", que deve ter maiusculas e minúsculas como duas palavras diferentes. Neste exemplo, "Ferramentas" e "FileName" será sinalizado.  
  
 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Altere a palavra para que ele é maiusculas e minúsculas corretas.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se ambas as partes da palavra composta reconhecidas pelo dicionário de ortografia e a intenção é usar duas palavras.  
  
 Você também pode adicionar palavras compostas de um dicionário personalizado para o verificador ortográfico. Palavras no dicionário personalizado não causam violações. Para obter mais informações, consulte [como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1702: palavras compostas devem ter maiúsculas e minúsculas corretas](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Consulte também  
 [Convenções de maiusculas e minúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Diretrizes de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)