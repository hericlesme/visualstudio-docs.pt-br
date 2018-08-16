---
title: 'CA2116: os métodos APTCA só devem chamar métodos APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70affcf0b71e9d0ae7440141f45f5ae0f2c04bf6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917613"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: os métodos APTCA só devem chamar métodos APTCA
|||
|-|-|
|NomeDoTipo|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método em um assembly com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo chama um método em um assembly que não tem o atributo.

## <a name="rule-description"></a>Descrição da Regra
 Por padrão, públicos ou protegidos métodos em assemblies com nomes fortes são implicitamente protegidos por um [demandas de Link](/dotnet/framework/misc/link-demands) de confiança total; somente confiáveis os chamadores podem acessar um assembly de nome forte. Assemblies de nomes fortes marcado com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) não tem essa proteção. O atributo desabilita a demanda de link, fazendo com que o assembly acessível para chamadores que não têm confiança total, como o código executado de uma intranet ou da Internet.

 Quando o atributo APTCA estiver presente em um assembly totalmente confiável, e o assembly executa código em outro assembly que não permite chamadores parcialmente confiáveis, um ataque de segurança é possível. Se dois métodos `M1` e `M2` atendem às seguintes condições, chamadores mal-intencionados podem usar o método `M1` para ignorar a demanda de link de confiança total implícito que protege `M2`:

-   `M1` um método público é declarado em um assembly totalmente confiável que tem o atributo APTCA.

-   `M1` chama um método `M2` fora `M1`do assembly.

-   `M2`do assembly não tem o atributo APTCA e, portanto, não devem ser executado, ou em nome de chamadores parcialmente confiáveis.

 Um chamador parcialmente confiável `X` pode chamar o método `M1`, causando `M1` chamar `M2`. Porque `M2` não tem o atributo APTCA, o chamador imediato (`M1`) devem atender a uma demanda de link de confiança total; `M1` tem confiança total e portanto satisfaz essa verificação. O risco de segurança é porque `X` não participar no que satisfazem a demanda de link que protege `M2` de chamadores não confiáveis. Portanto, os métodos com o atributo APTCA não devem chamar métodos que não têm o atributo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Se o atributo APCTA for necessário, use uma demanda para proteger o método que chama o assembly de confiança total. As permissões exatas dependerá de você demanda na funcionalidade exposta pelo método. Se for possível, proteja o método com uma solicitação de confiança total garantir que a funcionalidade subjacente não é exposta a chamadores parcialmente confiáveis. Se isso não for possível, selecione um conjunto de permissões que efetivamente protege a funcionalidade exposta.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para suprimir com segurança um aviso dessa regra, você deve garantir que a funcionalidade exposta pelo método não direta ou indiretamente permite chamadores acessem informações confidenciais, operações ou recursos que podem ser usados de forma destrutivas.

## <a name="example"></a>Exemplo
 O exemplo a seguir usa dois assemblies e um aplicativo de teste para ilustrar a vulnerabilidade de segurança detectada por essa regra. O primeiro conjunto não tem o atributo APTCA e não deve ser acessível para chamadores parcialmente confiáveis (representado por `M2` na discussão anterior).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example"></a>Exemplo
 O segundo conjunto é totalmente confiável e permite que os chamadores parcialmente confiáveis (representado por `M1` na discussão anterior).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example"></a>Exemplo
 O aplicativo de teste (representado por `X` na discussão anterior) é parcialmente confiável.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

 Este exemplo gerencia a seguinte saída.

 **Falha na demanda de confiança: solicitação completa. ** 
 **ClassRequiringFullTrust.DoWork foi chamado.**
## <a name="related-rules"></a>Regras relacionadas
 [CA2117: os tipos APTCA só devem estender tipos base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Consulte também
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines) [usando bibliotecas de parcialmente confiável código](/dotnet/framework/misc/using-libraries-from-partially-trusted-code) [demandas de Link](/dotnet/framework/misc/link-demands) [dados e modelagem](/dotnet/framework/data/index)