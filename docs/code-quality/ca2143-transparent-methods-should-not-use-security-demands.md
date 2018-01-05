---
title: "CA2143: Os métodos transparentes não devem usar demandas de segurança | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 073ce1d22662b46a19bf5cf36305df63500347a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: os métodos transparentes não devem usar demandas de segurança
|||  
|-|-|  
|NomeDoTipo|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método ou tipo tranparent declarativamente é marcado com um <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` demanda ou chamadas de método de <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> método.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O código transparente de segurança não deve ser responsável por verificar a segurança de uma operação e, assim, não deve exigir permissões. O código transparente de segurança deve usar demandas completas para tomar decisões de segurança e o código crítico de segurança não deve confiar no código transparente para fazer a demanda completa. Qualquer código que executa verificações de segurança, como demandas de segurança, em vez disso, deve ser crítico para segurança.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Em geral, para corrigir uma violação desta regra, marcar o método com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo. Você também pode remover a demanda.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 A regra de arquivos com o código a seguir como um método transparente torna uma exigência de segurança declarativa.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [CA2142: código transparente não deve ser protegido com LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)