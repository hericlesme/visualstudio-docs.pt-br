---
title: 'CA2204: Literais devem ser grafadas corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fca8484b3231a92ab3a425c4661229236833642
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: os literais do recurso devem ter a ortografia correta
|||  
|-|-|  
|NomeDoTipo|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Passa um método que uma cadeia de caracteres literal para o que é usada em um parâmetro ou uma propriedade que requer uma cadeia de caracteres localizada e a cadeia de caracteres literal contém uma ou mais palavras que não são reconhecidas pela biblioteca do verificador ortográfico do Microsoft.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra verifica se uma cadeia de caracteres literal que é passada como um valor para um parâmetro ou a propriedade quando um ou mais dos casos a seguir forem verdadeiras:  
  
-   O <xref:System.ComponentModel.LocalizableAttribute> atributo do parâmetro ou propriedade é definido como true.  
  
-   O nome de parâmetro ou a propriedade contém "Text", "Mensagem" ou "Legenda".  
  
-   O nome do parâmetro de cadeia de caracteres que é passado para um método Write ou console. WriteLine é "valor" ou "formato".  
  
 Esta regra analisa a cadeia de caracteres literal em palavras, tokens palavras compostas e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: os identificadores devem ser grafados corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Por padrão, a versão em inglês (en) do verificador ortográfico é usada.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, corrija a ortografia da palavra ou adicionar a palavra ao dicionário personalizado. Para obter informações sobre como usar os dicionários personalizados, consulte [como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Corretamente palavras reduzem a curva de aprendizado necessária para novas bibliotecas de software.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)