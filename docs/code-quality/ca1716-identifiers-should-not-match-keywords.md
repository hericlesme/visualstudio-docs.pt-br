---
title: 'CA1716: os identificadores não devem corresponder a palavras-chave'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 079a3502b35807fed39070b59c6ded2e554bf511
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: os identificadores não devem corresponder a palavras-chave
|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um nome de um namespace, um tipo ou um membro de interface ou viritual corresponde a uma palavra-chave reservada em uma linguagem de programação.

## <a name="rule-description"></a>Descrição da Regra
 Identificadores para namespaces, tipos e virtuais e membros de interface não devem corresponder a palavras-chave que são definidas por linguagens que direcionam o common language runtime. Dependendo do idioma usado e a palavra-chave, ambiguidades e erros do compilador podem dificultar a biblioteca a ser usado.

 Esta regra verifica em palavras-chave nos seguintes idiomas:

-   Visual Basic

-   C#

-   C++/CLI

 Comparação de maiusculas e minúsculas é usada para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] palavras-chave e a comparação diferencia maiusculas de minúsculas é usada para os outros idiomas.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Selecione um nome que não aparecem na lista de palavras-chave.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você pode suprimir um aviso de que essa regra se estiver convencido de que o identificador não será confundir os usuários da API e que a biblioteca é pode ser usada em todos os idiomas disponíveis no [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].