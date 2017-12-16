---
title: "CA2131: Os tipos críticos de segurança não podem participar no equivalência de tipo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 287004949e181ced6ffc04e0250f9fdff89d4318
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: os tipos críticos de segurança podem não participar da equivalência de tipo
|||  
|-|-|  
|NomeDoTipo|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo participa equivalência de tipo e um o tipo em si, ou um campo do tipo ou membro está marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra é acionada em qualquer tipo crítico ou em tipos que contenham métodos críticos ou campos que estejam participando da equivalência do tipo. Quando o CLR detecta desse tipo, não consiga carregá-lo com um <xref:System.TypeLoadException> em tempo de execução. Normalmente, essa regra só é acionada quando usuários implementam equivalência de tipo manualmente, em vez de depender de tlbimp e dos compiladores para fazer a equivalência do tipo.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo SecurityCritical.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir demonstram uma interface, um método e um campo que fará com que esta regra seja acionado.  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Código transparente de segurança, nível 2](/dotnet/framework/misc/security-transparent-code-level-2)