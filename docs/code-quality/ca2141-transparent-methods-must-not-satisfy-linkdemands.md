---
title: "CA2141: os métodos transparentes não devem atender a LinkDemands | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 938bda4d4b5c96b9627cf11aae81c51d269c0e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparent métodos não devem atender a LinkDemands
|||  
|-|-|  
|NomeDoTipo|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método transparente de segurança chama um método em um assembly que não está marcado com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) ou um método transparente de segurança satisfaz um <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` para um tipo ou um método.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Satisfazer um LinkDemand é uma operação de confidenciais de segurança que pode causar a não intencional de elevação de privilégio. Código transparente de segurança não deve atender a LinkDemands, porque ela não está sujeita a requisitos de auditoria de segurança como o código de segurança crítica. Os métodos transparentes em assemblies de nível 1 de conjunto de regras de segurança fará com que todas as LinkDemands atendem a ser convertido em demandas completas em tempo de execução, o que pode causar problemas de desempenho. Em assemblies de nível 2 de conjunto de regras de segurança, os métodos transparentes não serão compilado no compilador just-in-time (JIT), caso eles tentem satisfazer um LinkDemand.  
  
 Em assemblies que usee segurança de nível 2, tentativas de um método de segurança transparente para satisfazer um LinkDemand ou chamar um método em um assembly não-APTCA gera um <xref:System.MethodAccessException>; em assemblies de nível 1 de LinkDemand torna-se uma solicitação total.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o método de acesso com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> de atributo ou remover o LinkDemand do método acessado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, um método transparente tenta chamar um método que possui um LinkDemand. Essa regra será acionado nesse código.  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]