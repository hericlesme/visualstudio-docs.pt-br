---
title: "CA1801: Revisar parâmetros não usados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb8c38d1436ca687664f92bfe0ba6db1ccf68ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: revisar parâmetros não usados
|||  
|-|-|  
|NomeDoTipo|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis - se o membro não é visível fora do assembly, independentemente da alteração feita.<br /><br /> Não separáveis - se você alterar o membro para usar o parâmetro em seu corpo.<br /><br /> Quebrar - se que você remova o parâmetro e é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Uma assinatura de método inclui um parâmetro que não é usado no corpo do método. Esta regra examina os seguintes métodos:  
  
-   Métodos referenciados por um representante.  
  
-   Métodos usados como manipuladores de eventos.  
  
-   Métodos declarados com o `abstract` (`MustOverride` no Visual Basic) modificador.  
  
-   Métodos declarados com o `virtual` (`Overridable` no Visual Basic) modificador.  
  
-   Métodos declarados com o `override` (`Overrides` no Visual Basic) modificador.  
  
-   Métodos declarados com o `extern` (`Declare` instrução no Visual Basic) modificador.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Verifique os parâmetros em métodos não virtuais que não são usados no corpo do método para certificar-se de que nenhuma correção existe uma falha para acessá-los. Parâmetros não utilizados incorrem em custos de manutenção e desempenho.  
  
 Às vezes, uma violação desta regra pode apontar para um bug de implementação no método. Por exemplo, o parâmetro deve ter foi usado no corpo do método. Suprima avisos desta regra se o parâmetro precisar existir devido à compatibilidade com versões anteriores.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o parâmetro não utilizado (uma alteração significativa) ou use o parâmetro no corpo do método (uma alteração sem quebra).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra para o código fornecido anteriormente para os quais a correção seria uma alteração significativa.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois métodos. Um método viola a regra e o outro método satisfaz a regra.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)