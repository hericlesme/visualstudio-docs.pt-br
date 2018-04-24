---
title: 'CA1403: os tipos de layout automático não devem ser visíveis em COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2559f5d281a9669d2d36419eaeccd5ad879ce926
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: os tipos de layout automático não devem ser visíveis em COM
|||
|-|-|
|NomeDoTipo|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo de valor visível do modelo de objeto de componente (COM) está marcado com o <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atributo definido como <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Runtime.InteropServices.LayoutKind> tipos de layout são gerenciados pelo common language runtime. Pode alterar o layout desses tipos entre versões do .NET Framework, o que interromperá a clientes COM que espera um layout específico. Observe que, se o <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo não for especificado, o c#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e especifique os compiladores C++ a <xref:System.Runtime.InteropServices.LayoutKind> layout para tipos de valor.

 A menos que marcada caso contrário, todos os tipos de não-genéricos públicos são visíveis no COM; todos os tipos genéricos e confidenciais são visíveis para COM. No entanto, para reduzir o número de falsos positivos, essa regra requer a visibilidade de COM do tipo a ser declarado explicitamente; o assembly contendo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definida como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o valor da <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo <xref:System.Runtime.InteropServices.LayoutKind> ou <xref:System.Runtime.InteropServices.LayoutKind>, ou fazer com que o tipo invisível em COM.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra e um tipo que atenda a regra.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Consulte também
 [Qualificando tipos do .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interoperação com código não gerenciado](/dotnet/framework/interop/index)