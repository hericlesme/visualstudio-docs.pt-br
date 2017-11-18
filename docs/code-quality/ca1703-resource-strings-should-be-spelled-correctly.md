---
title: 'CA1703: as cadeias de caracteres de recurso devem ter grafia correta | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c7828aa218933208408a285510e998921d6f032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta
|||  
|-|-|  
|NomeDoTipo|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra analisa a cadeia de caracteres em palavras (tokens palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: os identificadores devem ser grafados corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Por padrão, a versão em inglês (en) do verificador ortográfico é usada.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, use palavras completas que estão escritas corretamente ou adicioná-las a um dicionário personalizado. Para obter informações sobre como usar os dicionários personalizados, consulte [CA1704: os identificadores devem ser grafados corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Corretamente palavras reduzem o tempo necessário para aprender novas bibliotecas de software.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)