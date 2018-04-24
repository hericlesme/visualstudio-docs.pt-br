---
title: 'CA2223: os membros devem ser diferentes além do tipo de retorno'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4caffc53ff99f20a0dee94990dd6f5b966f2e047
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: os membros devem ser diferentes além do tipo de retorno
|||
|-|-|
|NomeDoTipo|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Dois membros públicos ou protegidos tem assinaturas são idênticas, exceto o tipo de retorno.

## <a name="rule-description"></a>Descrição da Regra
 Embora o common language runtime permite o uso de tipos de retorno para diferenciar entre os membros idênticos, esse recurso não está no Common Language Specification, nem é um recurso comum das linguagens de programação .NET. Quando membros diferem somente por tipo de retorno, os desenvolvedores e ferramentas de desenvolvimento podem não corretamente distinção entre eles.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o design dos membros para que eles são exclusivos com base apenas em seus nomes e tipos de parâmetro ou não expõem os membros.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir, na Microsoft intermediate language (MSIL), mostra um tipo que violam essa regra. Observe que essa regra não pode ser violada usando c# ou Visual Basic.

```

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary

```