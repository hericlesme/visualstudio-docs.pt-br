---
title: "CA2114: A segurança de método deve ser um superconjunto do tipo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac633134b5b8037eb9e45131128b0ee0cf2887ab
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: a segurança de método deve ser um superconjunto de tipo
|||  
|-|-|  
|NomeDoTipo|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo tem segurança declarativa e um de seus métodos tem a segurança declarativa para a mesma ação de segurança e a ação de segurança não é [demandas de Link](/dotnet/framework/misc/link-demands), e as permissões são verificadas pelo tipo não são um subconjunto das permissões verificado pelo método.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um método não deve ter tanto uma tipo de nível e de método a segurança declarativa para a mesma ação. As duas verificações não são combinadas; somente a demanda de nível de método é aplicada. Por exemplo, se um tipo exige permissão `X`, e um de seus métodos exige permissão `Y`, código não precisa ter permissão `X` para executar o método.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Revise seu código para certificar-se de que ambas as ações são necessárias. Se ambas as ações forem necessárias, certifique-se de que a ação de nível de método inclui a segurança especificada no nível de tipo. Por exemplo, se seu tipo exige permissão `X`, e seu método também deve solicitar permissão `Y`, o método deve solicitar explicitamente `X` e `Y`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o método não exigir que o especificado pelo tipo de segurança. No entanto, isso não é um cenário comum e pode indicar a necessidade de uma revisão do design cuidadoso.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa permissões do ambiente para demonstrar os perigos de violam essa regra. Neste exemplo, o código do aplicativo cria uma instância do tipo seguro antes de negar a permissão exigida pelo tipo. Em um cenário de ameaças do mundo real, o aplicativo requer outra maneira de obter uma instância do objeto.  
  
 No exemplo a seguir, as demandas de biblioteca permissão de gravação para um tipo em a permissão de leitura para um método.  
  
 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O código de aplicativo a seguir demonstra a vulnerabilidade da biblioteca chamando o método, mesmo que ele não atende ao requisito de segurança em nível de tipo.  
  
 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **[Todas as permissões] Informações pessoais: 16/6/1964 12:00:00 AM**  
**[Nenhuma permissão de gravação (exigido por tipo)] Informações pessoais: 16/6/1964 12:00:00 AM**  
**[Nenhuma permissão de leitura (exigido pelo método)] Não foi possível acessar as informações pessoais: Falha na solicitação.**   
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Demandas de link](/dotnet/framework/misc/link-demands)   
 [Dados e modelagem](/dotnet/framework/data/index)