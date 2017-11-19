---
title: "CA1804: Remover locais não usados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9217f3109c6ef03de33e444e723caa585d065efb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: remover locais não usados
|||  
|-|-|  
|NomeDoTipo|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um método declara uma variável local, mas não use a variável exceto possivelmente como o destinatário de uma instrução de atribuição. Para análise por essa regra, o assembly testado deve ser compilado com as informações de depuração e o arquivo de banco de dados (. PDB) do programa associado deve estar disponível.  
  
## <a name="rule-description"></a>Descrição da Regra  
 As variáveis locais não utilizadas e as atribuições desnecessárias aumentam o tamanho de um assembly e diminuem o desempenho.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova ou use a variável local. Observe que o compilador c# que é incluído com [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] remove variáveis locais não utilizadas quando o `optimize` opção é habilitada.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra se a variável foi emitido do compilador. Também é seguro para suprimir um aviso dessa regra, ou para desabilitar a regra, se o desempenho e manutenção de código não são principais preocupações.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra várias variáveis locais não utilizadas.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1809: evitar locais excessivos](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: examinar parâmetros não usados](../code-quality/ca1801-review-unused-parameters.md)