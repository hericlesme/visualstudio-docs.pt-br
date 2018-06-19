---
title: 'CA1017: marcar assemblies com ComVisibleAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf6ea87a1a84f5c9f527b0d0c2550093d8824152
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899138"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: marcar assemblies com ComVisibleAttribute
|||
|-|-|
|NomeDoTipo|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um assembly não tem o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo aplicado a ele.

## <a name="rule-description"></a>Descrição da Regra
 O <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina como os clientes COM acessam a código gerenciado. Um bom design determina que os assemblies indiquem explicitamente a visibilidade de COM. Visibilidade COM pode ser definida para um conjunto inteiro e, em seguida, substituída para individuais tipos e membros de tipo. Se o atributo não estiver presente, o conteúdo do assembly é visível para clientes COM.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione o atributo para o assembly. Se você não quiser que o assembly seja visível para clientes COM, aplique o atributo e defina seu valor como `false`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Se você quiser que o assembly esteja visível, aplique o atributo e defina seu valor como `true`.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um assembly que tem o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo aplicado para impedir que ele seja visível para clientes COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Consulte também
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index) [qualificando tipos do .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)