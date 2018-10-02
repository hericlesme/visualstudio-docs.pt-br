---
title: 'CA1722: Os identificadores não devem ter prefixo incorreto | Microsoft Docs'
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
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83843a7713adf3d0c3680470df05bb378c797d38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587247"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: os identificadores não devem ter prefixo incorreto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1722: os identificadores não devem ter prefixo incorreto](https://docs.microsoft.com/visualstudio/code-quality/ca1722-identifiers-should-not-have-incorrect-prefix).

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um identificador tem um prefixo incorreto.

## <a name="rule-description"></a>Descrição da Regra
 Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.

 Nomes de tipo não têm um prefixo específico e não devem ser prefixados com um 'c'. Esta regra relata violações para nomes de tipo como 'CMyClass' e não relata violações para nomes de tipo como 'Cache'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova o prefixo do identificador.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1715: os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)



