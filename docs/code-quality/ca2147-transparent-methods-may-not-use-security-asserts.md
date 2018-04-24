---
title: 'CA2147: os métodos transparentes talvez não usem declarações de segurança'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a095bb50c23600aa04959db670a4038bd18cbaf1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: os métodos transparentes talvez não usem declarações de segurança
|||
|-|-|
|NomeDoTipo|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Código que está marcado como <xref:System.Security.SecurityTransparentAttribute> não tem permissões suficientes para assert.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra analisa todos os métodos e tipos em um assembly que é a 100% transparente ou misto transparente crítica e sinaliza qualquer uso declarativo ou imperativo de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 No tempo de execução, todas as chamadas para <xref:System.Security.CodeAccessPermission.Assert%2A> do código de transparência fará com que um <xref:System.InvalidOperationException> seja gerada. Isso pode ocorrer em ambos os assemblies transparente de 100% e também em assemblies mistos transparente críticos onde um método ou tipo é declarado transparente, mas inclui uma asserção declarativa ou obrigatória.

 O [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 introduziu um recurso chamado *transparência*. Tipos, campos, interfaces, classes e métodos individuais podem ser transparente ou crítico.

 Código transparente não é permitido para elevar os privilégios de segurança. Portanto, todas as permissões concedidas ou exigidos dele automaticamente são passadas por meio do código para o domínio de aplicativo do chamador ou host. Elevações exemplos de declarações, LinkDemands, SuppressUnmanagedCode, e `unsafe` código.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para resolver o problema, uma marca o código que chama o Assert com o <xref:System.Security.SecurityCriticalAttribute>, ou remover o Assert.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima uma mensagem dessa regra.

## <a name="example"></a>Exemplo
 Este código falhará se `SecurityTestClass` é transparente, quando o `Assert` método lança um <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Exemplo
 Uma opção é o método SecurityTransparentMethod no exemplo a seguir de revisão de código e se o método é considerado seguro para elevação, marcar SecurityTransparentMethod com segurança crítica isso requer que um detalhadas, completa e livre de erro de segurança auditoria deve ser executada no método junto com qualquer explicativo que ocorrem dentro do método em Assert:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Outra opção é remover o Assert do código e permitir que qualquer arquivo subsequente fluxo de demandas de permissão e/s além SecurityTransparentMethod ao chamador. Isso permite que as verificações de segurança. Nesse caso, nenhuma auditoria de segurança geralmente é necessário, porque as demandas de permissão fluirá para o chamador e/ou o domínio de aplicativo. Demandas de permissão em conjunto são controladas pela política de segurança e hospedagem de ambiente e concessões de permissão do código-fonte.

## <a name="see-also"></a>Consulte também
 [Avisos de segurança](../code-quality/security-warnings.md)