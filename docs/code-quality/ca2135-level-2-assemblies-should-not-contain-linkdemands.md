---
title: "CA2135: Os assemblies de nível 2 não devem conter LinkDemands | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea4d0adf3573410c9f8a25e6b5d3abf2615c8ad3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: os assemblies de nível 2 não devem conter LinkDemands
|||  
|-|-|  
|NomeDoTipo|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Uma classe ou membro de classe está usando um <xref:System.Security.Permissions.SecurityAction> em um aplicativo que está usando a segurança de nível 2.  
  
## <a name="rule-description"></a>Descrição da Regra  
 LinkDemands são preteridos no conjunto de regras de segurança nível 2. Em vez de usar LinkDemands para aplicar a segurança em tempo de compilação just-in-time (JIT), marque os métodos, tipos e campos com o <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o <xref:System.Security.Permissions.SecurityAction> e marcar o tipo ou membro com o <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Security.Permissions.SecurityAction> devem ser removidos e o método marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]