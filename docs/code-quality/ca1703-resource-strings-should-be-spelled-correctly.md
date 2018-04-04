---
title: 'CA1703: as cadeias de caracteres de recurso devem ter grafia correta | Microsoft Docs'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1227849992cf91a208563020583b19af48b13d42
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
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

## <a name="rule-description"></a>Descrição da regra

Esta regra analisa a cadeia de caracteres em palavras (tokens palavras compostas) e verifica a ortografia de cada palavra/token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: os identificadores devem ser grafados corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação desta regra, use palavras completas que estão escritas corretamente ou adicioná-las a um dicionário personalizado. Para obter informações sobre como usar os dicionários personalizados, consulte [CA1704: os identificadores devem ser grafados corretamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Alterar o idioma do dicionário

Por padrão, a versão em inglês (en) do verificador ortográfico é usada. Se você quiser alterar o idioma do verificador ortográfico, você poderá fazê-lo adicionando um dos seguintes atributos para o *AssemblyInfo.cs* ou *AssemblyInfo* arquivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar a cultura se os recursos estão em um assembly satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar o *cultura neutra* do seu assembly se os recursos estão no mesmo assembly como o seu código.

> [!IMPORTANT]
> Se você definir a cultura para algo diferente de uma cultura baseada em inglês, esta regra de análise de código silenciosamente está desabilitada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Corretamente palavras reduzem o tempo necessário para aprender novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas

- [CA1701: as palavras compostas da cadeia de caracteres de recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: os identificadores devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: os literais devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)