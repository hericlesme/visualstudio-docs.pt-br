---
title: 'CA1414: Marcar argumentos de P-Invoke boolianos com MarshalAs | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5753affc1f635e322d17ea10617297d3ec71077a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587137"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: marcar argumentos P/Invoke boolianos com MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1414: marcar argumentos de P-Invoke boolianos com MarshalAs](https://docs.microsoft.com/visualstudio/code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas).

|||
|-|-|
|NomeDoTipo|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma plataforma de invocação de método de declaração inclui um <xref:System.Boolean?displayProperty=fullName> parâmetro ou valor retornado, mas o <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atributo não é aplicado ao valor de parâmetro ou retornado.

## <a name="rule-description"></a>Descrição da Regra
 Uma plataforma de chamar código não gerenciado do método acessos e é definido usando o `Declare` palavra-chave na [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Especifica o comportamento de marshaling que é usado para converter tipos de dados entre código gerenciado e não gerenciado. Tipos de muitos dados simples, como <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, ter uma única representação em código não gerenciado e não exigem a especificação de seu comportamento de marshaling; o common language runtime fornece o comportamento correto automaticamente.

 O <xref:System.Boolean> tipo de dados tem várias representações em código não gerenciado. Quando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> não for especificado, o padrão de empacotamento de comportamento para o <xref:System.Boolean> tipo de dados é <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Isso é um inteiro de 32 bits, que não é apropriado em todas as circunstâncias. A representação de booliana é necessário para o método não gerenciado deve ser determinada e combinada para apropriado <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool é o tipo BOOL Win32, que é sempre de 4 bytes. UnmanagedType.U1 deve ser usado para C++ `bool` ou outros tipos de 1 byte. Para obter mais informações, consulte [Marshaling padrão para tipos boolianos](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> para o <xref:System.Boolean> parâmetro ou valor retornado. Defina o valor do atributo como apropriado <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Mesmo se o comportamento de marshaling padrão é apropriado, o código mais facilmente é mantido quando o comportamento é especificado explicitamente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra os métodos que são marcados com os devidos a invocação de plataforma dois <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributos.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1901: as declarações P/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Marshaling padrão para tipos boolianos](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [interoperação com código não gerenciado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



