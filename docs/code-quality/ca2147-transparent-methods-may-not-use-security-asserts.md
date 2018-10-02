---
title: 'CA2147: os métodos transparentes talvez não usem declarações de segurança'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: ca9047866b5b8f030ee8e1f5a043683234edeb72
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859530"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: os métodos transparentes talvez não usem declarações de segurança
|||
|-|-|
|NomeDoTipo|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Código que está marcado como <xref:System.Security.SecurityTransparentAttribute> não tem permissões suficientes para declarar.

## <a name="rule-description"></a>Descrição da regra
 Esta regra analisa todos os métodos e tipos em um assembly que é qualquer um dos 100% transparente ou misto transparente/crítico e sinaliza qualquer uso declarativo ou obrigatório do <xref:System.Security.CodeAccessPermission.Assert%2A>.

 No tempo de execução, todas as chamadas para <xref:System.Security.CodeAccessPermission.Assert%2A> no código transparent fará com que um <xref:System.InvalidOperationException> seja lançada. Isso pode ocorrer em ambos os assemblies de 100% transparente e também em assemblies mistos transparente/crítico em que um tipo ou método é declarado transparente, mas inclui um Assert declarativa ou imperativa.

 O .NET Framework 2.0 introduziu um recurso denominado *transparência*. Tipos, campos, interfaces, classes e métodos individuais podem ser transparente ou crítica.

 O código transparente não é permitido para elevar privilégios de segurança. Portanto, todas as permissões concedidas ou exigidas dele automaticamente são passadas por meio do código para o domínio de aplicativo do chamador ou o host. As elevações exemplos de declarações, LinkDemands, SuppressUnmanagedCode, e `unsafe` código.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para resolver o problema, a marcar o código que chama o Assert com o <xref:System.Security.SecurityCriticalAttribute>, ou remover o Assert.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima uma mensagem a partir dessa regra.

## <a name="example"></a>Exemplo
 Este código falhará caso `SecurityTestClass` é transparente, quando o `Assert` método lança um <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Exemplo
 Uma opção é o método SecurityTransparentMethod no exemplo a seguir de revisão de código e se o método é considerado seguro para elevação, marque SecurityTransparentMethod com seguro-crítica. Isso requer que uma auditoria de segurança detalhada, completo e livre de erros deve ser executada no método junto com qualquer explicativos que ocorrem dentro do método em Assert:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Outra opção é remover o Assert do código e permitir que qualquer arquivo subsequente de fluxo de demandas de permissão e/s além SecurityTransparentMethod ao chamador. Isso permite que verificações de segurança. Nesse caso, nenhuma auditoria de segurança é necessária, porque as demandas de permissão fluirão para o chamador e/ou o domínio do aplicativo. Demandas de permissão de perto são controladas pela política de segurança, concessões de permissão de código-fonte e ambiente de hospedagem.

## <a name="see-also"></a>Consulte também
 [Avisos de segurança](../code-quality/security-warnings.md)