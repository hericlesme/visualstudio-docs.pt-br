---
title: 'CA1707: os identificadores não devem conter sublinhados'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4eed69f8c08d6106bf30e9c1884512e384a7a269
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: os identificadores não devem conter sublinhados
|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra - quando gerado em assemblies<br /><br /> Separação de não - quando gerado em parâmetros de tipo|

## <a name="cause"></a>Causa
 O nome de um identificador contém o caractere de sublinhado (_).

## <a name="rule-description"></a>Descrição da Regra
 Por convenção, os nomes de identificador não contêm o caractere de sublinhado (_). A regra verifica os namespaces, tipos, membros e parâmetros.

 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova todos os caracteres de sublinhado no nome.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)