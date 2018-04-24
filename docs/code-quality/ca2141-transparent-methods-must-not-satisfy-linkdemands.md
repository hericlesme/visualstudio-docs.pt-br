---
title: CA2141:Transparent métodos não devem atender a LinkDemands
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a64e8acae7e7dd76107bc761a6b035f2963247fe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
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