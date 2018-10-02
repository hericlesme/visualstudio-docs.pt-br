---
title: 'CA1703: as cadeias de caracteres de recurso devem ter grafia correta | Microsoft Docs'
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
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fc83d109666c98718b1a4b1196db11a81424c911
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587151"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1703: as cadeias de caracteres de recurso devem ter grafia correta](https://docs.microsoft.com/visualstudio/code-quality/ca1703-resource-strings-should-be-spelled-correctly).

|||
|-|-|
|NomeDoTipo|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma cadeia de caracteres de recurso contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra analisa a cadeia de caracteres de recurso em palavras (criar tokens de palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: os identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Por padrão, a versão em inglês (en) do verificador ortográfico é usada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, use palavras completas que estão escritas corretamente ou adicioná-las a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, consulte [CA1704: os identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Corretamente as palavras escritas de reduzem o tempo necessário para aprender novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas
 [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)



