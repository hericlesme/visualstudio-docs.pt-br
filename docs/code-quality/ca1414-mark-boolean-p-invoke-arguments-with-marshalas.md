---
title: 'CA1414: Marcar argumentos P Invoke boolianos com MarshalAs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19536941f0b4b3d96255cb9eb323bea5d4e899bf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916195"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: marcar argumentos P/Invoke boolianos com MarshalAs
|||
|-|-|
|NomeDoTipo|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma plataforma de invocar o método de declaração inclui um <xref:System.Boolean?displayProperty=fullName> valor de parâmetro ou retornado, mas o <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atributo não é aplicado ao valor de parâmetro ou retornado.

## <a name="rule-description"></a>Descrição da Regra
 Uma plataforma de chamar código não gerenciado do método acessa e é definido usando o `Declare` palavra-chave em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Especifica o comportamento de marshaling que é usado para converter tipos de dados entre código gerenciado e não gerenciado. Tipos de muitos dados simples, como <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, ter uma única representação em código não gerenciado e não exigem a especificação de seu comportamento de marshaling; o common language runtime fornece automaticamente o comportamento correto.

 O <xref:System.Boolean> tipo de dados tem várias representações em código não gerenciado. Quando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> não for especificado, o padrão de empacotamento de comportamento para o <xref:System.Boolean> é do tipo de dados <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Este é um inteiro de 32 bits, que não é apropriado em todas as circunstâncias. A representação de booliana que é exigida pelo método de não gerenciado deve ser determinada e correspondeu ao apropriado <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool é o tipo BOOL Win32, que sempre é de 4 bytes. UnmanagedType.U1 devem ser usados para C++ `bool` ou outros tipos de 1 byte.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, aplicar <xref:System.Runtime.InteropServices.MarshalAsAttribute> para o <xref:System.Boolean> parâmetro ou do valor retornado. Defina o valor do atributo como apropriada <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Mesmo que o comportamento de marshaling padrão é apropriado, o código mais facilmente é mantido quando o comportamento é especificado explicitamente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra os métodos que são marcados com apropriada de invocação de plataforma dois <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributos.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1901: Declarações P/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Interoperação com código não gerenciado](/dotnet/framework/interop/index)