---
title: "CA1720: Os identificadores não devem conter nomes de tipo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5418bc8d265c32057911df2d3a15aaddacf1398e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: os identificadores não devem conter nomes de tipo
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 O nome de um parâmetro em um membro visível externamente contém um nome de tipo de dados.  
  
 -ou-  
  
 O nome de um membro visível externamente contém um nome de tipo de dados específicos de idioma.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Nomes de parâmetros e membros são melhor usados para se comunicar seu significado que to descrevem o tipo, o que deve ser fornecido pelas ferramentas de desenvolvimento. Nomes de membros, se um nome de tipo de dados deve ser usado, use um nome de independente da linguagem em vez de um idioma específico. Por exemplo, em vez do c# tipo nome 'int', use o nome de tipo de dados independente de idioma, Int32.  
  
 Cada token discreto no nome do parâmetro ou um membro é verificado em relação os seguintes nomes de tipo de dados específicos de idioma, de uma maneira de maiusculas e minúsculas:  
  
-   bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Abreviado  
  
-   UShort  
  
-   int  
  
-   UInt  
  
-   Inteiro  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Não assinado  
  
-   Assinado  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 Além disso, os nomes de parâmetro também são verificados contra os seguintes nomes de tipo de dados independente de idioma, de uma maneira de maiusculas e minúsculas:  
  
-   Objeto  
  
-   obj  
  
-   Boolean  
  
-   Char  
  
-   Cadeia de caracteres  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   PTR  
  
-   Ponteiro  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Simples  
  
-   Duplo  
  
-   Decimal  
  
-   GUID  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 **Se acionado em relação a um parâmetro:**  
  
 Substitua o identificador de tipo de dados no nome do parâmetro com um termo que descreve melhor seu significado ou um termo mais genérico, como 'value'.  
  
 **Se acionado em relação a um membro:**  
  
 Substitua o identificador de tipo de dados específicos de idioma no nome do membro com um termo que descreve melhor seu significado, um equivalente independente de idioma ou um termo mais genérico, como 'value'.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Uso ocasional de nomes de parâmetro e o membro de tipo pode ser apropriado. No entanto, para novos desenvolvimentos, nenhum conhecidos situações ocorrer onde você deve suprimir um aviso dessa regra. Para bibliotecas que têm anterior fornecido, você terá que suprimir um aviso dessa regra.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)