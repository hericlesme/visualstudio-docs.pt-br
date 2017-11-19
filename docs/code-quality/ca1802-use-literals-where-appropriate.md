---
title: 'CA1802: Usar literais quando apropriado | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 66ee20e099de0206664390623b7a50c5fec723a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: usar literais quando apropriado
|||  
|-|-|  
|NomeDoTipo|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um campo está declarado `static` e `readonly` (`Shared` e `ReadOnly` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e é inicializada com um valor que é computáveis em tempo de compilação.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O valor de um `static``readonly` campo é calculado em tempo de execução quando o construtor estático para o tipo de declaração é chamado. Se o `static``readonly` campo é inicializado quando é declarado e um construtor estático não é declarado explicitamente, o compilador emite um construtor estático para inicializar o campo.  
  
 O valor de um `const` campo é calculado em tempo de compilação e armazenado nos metadados, que aumenta o desempenho de tempo de execução quando ele é comparado com um `static``readonly` campo.  
  
 Como o valor atribuído ao campo de destino é computáveis em tempo de compilação, altere a declaração para um `const` campo para que o valor é computado em tempo de compilação em vez de em tempo de execução.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua o `static` e `readonly` modificadores com o `const` modificador.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra ou desabilitar a regra, se o desempenho não for um problema.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo `UseReadOnly`, que viola a regra e um tipo, `UseConstant`, que atende a regra.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]