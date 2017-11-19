---
title: "CA2117: Os tipos APTCA só devem estender tipos base APTCA | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5619de2512e18cbe9d7dbfb3d992886ae23a25bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: os tipos APTCA só devem estender tipos base APTCA
|||  
|-|-|  
|NomeDoTipo|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou protegido em um assembly com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo herda de um tipo declarado em um assembly que não tem o atributo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Por padrão, os tipos públicos ou protegidos em assemblies com nomes fortes implicitamente são protegidos por um [demandas de herança](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) de confiança total. Assemblies de nomes fortes marcado com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) não tem essa proteção. O atributo desabilita a demanda de herança. Isso torna expostos tipos declarados no assembly herdados por tipos que não têm confiança total.  
  
 Quando o atributo APTCA estiver presente em um assembly totalmente confiável, e um tipo no assembly herda de um tipo que não permite chamadores parcialmente confiáveis, um ataque de segurança é possível. Se dois tipos `T1` e `T2` atendem às seguintes condições, chamadores mal-intencionados podem usar o tipo `T1` para ignorar a demanda de herança de confiança total implícito que protege `T2`:  
  
-   `T1`um tipo público é declarado em um assembly totalmente confiável que tem o atributo APTCA.  
  
-   `T1`herda de um tipo `T2` fora de seu assembly.  
  
-   `T2`do assembly não tem o atributo APTCA e, portanto, não deve ser herdado pelos tipos em assemblies parcialmente confiáveis.  
  
 Um tipo parcialmente confiável `X` pode herdar de `T1`, que fornece acesso a membros herdados declarados em `T2`. Porque `T2` não tem o atributo APTCA, seu tipo derivado imediato (`T1`) devem atender a uma demanda de herança de confiança total; `T1` tem confiança total e portanto satisfaz essa verificação. O risco de segurança é porque `X` não participar no que satisfazem a demanda de herança que protege `T2` de subclassificação não confiável. Por esse motivo, tipos com o atributo APTCA não devem estender tipos que não têm o atributo.  
  
 Outro problema de segurança e talvez uma mais comum, é que o tipo derivado (`T1`) pode, por meio de erro do programador, expõe membros protegidos do tipo que requer confiança total (`T2`). Quando isso ocorrer, chamadores não confiáveis acessem informações que devem estar disponíveis somente para tipos totalmente confiáveis.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Se o tipo relatado pela violação está em um assembly que não requer o atributo APTCA, removê-lo.  
  
 Se o atributo APTCA é necessário, adicione uma demanda de herança de confiança total para o tipo. Isso protege contra a herança de tipos não confiáveis.  
  
 É possível corrigir uma violação, adicionando o atributo APTCA para os assemblies dos tipos de base relatados pela violação. Fazer isso sem primeiro conduzir uma revisão de segurança de uso intensivo de todo o código no assembly e todo o código que depende dos assemblies.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Para suprimir com segurança um aviso dessa regra, você deve garantir que membros protegidos expostos pelo seu tipo não direta ou indiretamente permitem chamadores não confiáveis acessar informações confidenciais, operações ou recursos que podem ser usados de forma destrutivas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa dois assemblies e um aplicativo de teste para ilustrar a vulnerabilidade de segurança detectada por essa regra. O primeiro conjunto não tem o atributo APTCA e não deve ser herdado pelos tipos parcialmente confiáveis (representado por `T2` na discussão anterior).  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O segundo conjunto, representado pelo `T1` na discussão anterior, é totalmente confiável e permite que os chamadores parcialmente confiáveis.  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>Exemplo  
 O tipo de teste, representado pelo `X` na discussão anterior, está em um assembly parcialmente confiável.  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **Atender no glen duvidoso 22/2/2003 12:00:00 AM!**  
**Ensolarado Campina de teste:**  
**Atender à Campina ensolarada 22/2/2003 12:00:00 AM!**   
## <a name="related-rules"></a>Regras relacionadas  
 [CA2116: os métodos APTCA só devem chamar métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Assemblies do .NET framework que pode ser chamados por código parcialmente confiável](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Usando Bibliotecas de Código Parcialmente Confiável](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
 [Demandas de herança](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)