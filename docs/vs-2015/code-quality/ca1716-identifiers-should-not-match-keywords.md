---
title: 'CA1716: Os identificadores não devem corresponder a palavras-chave | Microsoft Docs'
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
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1a3affbecf7a39ee323fd64bc8a56d92e8a4d5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586999"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: os identificadores não devem corresponder a palavras-chave
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1716: os identificadores não devem corresponder a palavras-chave](https://docs.microsoft.com/visualstudio/code-quality/ca1716-identifiers-should-not-match-keywords).

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um nome de um namespace, um tipo ou membro viritual ou interface corresponde a uma palavra-chave reservada em uma linguagem de programação.

## <a name="rule-description"></a>Descrição da Regra
 Identificadores de namespaces, tipos e virtuais e os membros de interface não devem corresponder a palavras-chave que são definidas por linguagens que visam o common language runtime. Dependendo da linguagem que é usada e a palavra-chave, ambiguidades e erros do compilador podem dificultar a biblioteca usar.

 Esta regra verifica em palavras-chave nos seguintes idiomas:

-   Visual Basic

-   C#

-   C++/CLI

 Comparação de maiusculas e minúsculas é usada para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] comparação diferencia maiusculas de minúsculas e palavras-chave é usada para os outros idiomas.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Selecione um nome que não aparece na lista de palavras-chave.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você pode suprimir um aviso nessa regra, se você estiver convencido de que o identificador não confundir os usuários da API, e que a biblioteca é utilizável em todos os idiomas disponíveis no [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].



