---
title: 'CA1408: não usar AutoDual ClassInterfaceType'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f324eee1ae71f063ddd19d5a7f3d82af6f45c00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: não usar AutoDual ClassInterfaceType
|||
|-|-|
|NomeDoTipo|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo de modelo de objeto de componente (COM) visível é marcado com o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo definido como o `AutoDual` valor <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Descrição da Regra
 Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo não for especificado, uma interface somente de expedição é usada.

 A menos que marcada caso contrário, todos os tipos de não-genéricos públicos são visíveis no COM; todos os tipos genéricos e confidenciais são visíveis para COM.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o valor da <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> de atributo para o `None` valor <xref:System.Runtime.InteropServices.ClassInterfaceType> e definir explicitamente a interface.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso dessa regra, a menos que você tiver certeza de que o layout do tipo e seus tipos base não será alterado em uma versão futura.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma classe que viola a regra e uma nova declaração de classe para usar uma interface explícita.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1403: os tipos de layout automático não devem ser visíveis em COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: marcar interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Consulte também
 [Qualificando tipos do .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interoperação com código não gerenciado](/dotnet/framework/interop/index)