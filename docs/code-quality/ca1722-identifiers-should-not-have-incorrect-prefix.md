---
title: "CA1722: Os identificadores não devem ter prefixo incorreto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 84cf14fc28a3de1d6ff5bff9e40216953d5d1461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: os identificadores não devem ter prefixo incorreto
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
  
 Nomes de tipo não tem um prefixo específico e não devem ser prefixados com um 'c'. Esta regra relata violações para nomes de tipo, como 'CMyClass' e não relata violações para nomes de tipo como 'Cache'.  
  
 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Remova o prefixo do identificador.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1715: os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)