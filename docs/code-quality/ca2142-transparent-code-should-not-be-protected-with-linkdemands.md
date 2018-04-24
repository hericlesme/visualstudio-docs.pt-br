---
title: 'CA2142: o código transparente não deve ser protegido com LinkDemands'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58f0c934c029c65a07fd0e89a5822dbbe0849428
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: o código transparente não deve ser protegido com LinkDemands
|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente exige um <xref:System.Security.Permissions.SecurityAction> ou outra exigência de segurança.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra é acionada em métodos transparentes que exigem LinkDemands para serem acessados. O código transparente de segurança não deve ser responsável por verificar a segurança de uma operação e, assim, não deve exigir permissões. Porque os métodos transparentes devem para ser segurança neutra, eles deverão não tomar decisões de segurança. Além disso, código crítico seguro, que toma decisões de segurança, não deve ser confiável no código transparente para feitas anteriormente essa decisão.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova a demanda de link no método transparente ou marcar o método com <xref:System.Security.SecuritySafeCriticalAttribute> verificações de atributo se ele estiver executando a segurança, como as exigências de segurança.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir, a regra dispara no método porque o método é transparente e está marcado com um LinkDemand <xref:System.Security.PermissionSet> que contém um <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 Não suprima um aviso nessa regra.