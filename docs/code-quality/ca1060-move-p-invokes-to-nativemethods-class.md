---
title: 'CA1060: Mover P-invoca a classe NativeMethods | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb93a44eebd9380499394c612ee12c40d0c62271
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: mover P/Invokes para a classe NativeMethods
|||  
|-|-|  
|NomeDoTipo|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método usa serviços de invocação de plataforma para acessar código não gerenciado e não é um membro de uma a **NativeMethods** classes.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Métodos de invocação de plataforma, como aqueles que são marcados com o uso de <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo ou métodos que são definidos usando o `Declare` palavra-chave em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], acessar código não gerenciado. Esses métodos devem estar em uma das seguintes classes:  
  
-   **NativeMethods** -essa classe não suprime as movimentações de pilha para permissão de código não gerenciado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> não devem ser aplicadas a essa classe.) Essa classe é para métodos que podem ser usados em qualquer lugar, porque um exame da pilha será executado.  
  
-   **SafeNativeMethods** -suprime a essa classe de movimentações de pilha para permissão de código não gerenciado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> é aplicado a essa classe.) Essa classe é para métodos que são seguros para qualquer pessoa chamar. Os chamadores desses métodos não serão necessário executar uma revisão de segurança completa para certificar-se de que o uso é seguro porque os métodos são inofensivos para qualquer chamador.  
  
-   **UnsafeNativeMethods** -suprime a essa classe de movimentações de pilha para permissão de código não gerenciado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> é aplicado a essa classe.) Essa classe é para métodos que são potencialmente perigosos. Qualquer chamador destes métodos deve executar uma revisão de segurança completa para certificar-se de que o uso é seguro porque nenhuma movimentação de pilha será executada.  
  
 Essas classes são declaradas como `internal` (`Friend`, no Visual Basic) e declarar um construtor particular para impedir que novas instâncias que está sendo criado. Os métodos nessas classes devem ser `static` e `internal` (`Shared` e `Friend` no Visual Basic).  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, acesse o método apropriado **NativeMethods** classe. Para a maioria dos aplicativos, mover P/Invokes para uma nova classe chamada **NativeMethods** é suficiente.  
  
 No entanto, se você estiver desenvolvendo bibliotecas para uso em outros aplicativos, você deve considerar definir duas outras classes que são chamados **SafeNativeMethods** e **UnsafeNativeMethods**. Essas classes são semelhantes a **NativeMethods** classe; no entanto, eles são marcados com o uso de um atributo especial chamado **SuppressUnmanagedCodeSecurityAttribute**. Quando esse atributo é aplicado, o tempo de execução não executará um exame da pilha completa para certificar-se de que todos os chamadores têm o **UnmanagedCode** permissão. O tempo de execução normalmente verifica essa permissão na inicialização. Como a verificação não é executada, ele pode aprimorar o desempenho de chamadas para esses métodos não gerenciados, ele também permite que o código que tem permissões limitadas para chamar esses métodos.  
  
 No entanto, você deve usar esse atributo com muito cuidado. Ele pode ter sérias implicações de segurança se for implementado incorretamente.  
  
 Para obter informações sobre como implementar os métodos, consulte o **NativeMethods** exemplo, **SafeNativeMethods** exemplo, e **UnsafeNativeMethods** exemplo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara um método que viola essa regra. Para corrigir a violação, a **RemoveDirectory** P/Invoke devem ser movido para uma classe apropriada que foi projetada para manter somente P/Invokes.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## <a name="nativemethods-example"></a>Exemplo de NativeMethods  
  
### <a name="description"></a>Descrição  
 Porque o **NativeMethods** classe não deve ser marcada usando **SuppressUnmanagedCodeSecurityAttribute**, P/Invokes são colocados nela exigirá **UnmanagedCode** permissão. Porque a maioria dos aplicativos executados no computador local e executar com confiança total, isso geralmente não é um problema. No entanto, se você estiver desenvolvendo bibliotecas reutilizáveis, você deve considerar definir uma **SafeNativeMethods** ou **UnsafeNativeMethods** classe.  
  
 A exemplo a seguir mostra um **Interaction.Beep** método que encapsula o **MessageBeep** função na User32. dll. O **MessageBeep** P/Invoke é colocada no **NativeMethods** classe.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## <a name="safenativemethods-example"></a>Exemplo de SafeNativeMethods  
  
### <a name="description"></a>Descrição  
 Métodos P/Invoke, que pode ser exposta com segurança para qualquer aplicativo e que não têm efeitos colaterais devem ser colocados em uma classe denominada **SafeNativeMethods**. Você não tem permissões de demanda e você não precisa preste muita atenção em que eles são chamados de.  
  
 A exemplo a seguir mostra um **TickCount** propriedade que encapsula o **ObterContagemMarcaEscala** função Kernel32.  
  
### <a name="code"></a>Código  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## <a name="unsafenativemethods-example"></a>Exemplo de UnsafeNativeMethods  
  
### <a name="description"></a>Descrição  
 Métodos P/Invoke, que não pode ser chamado com segurança e que pode causar efeitos colaterais devem ser colocados em uma classe denominada **UnsafeNativeMethods**. Esses métodos devem ser verificados rigorosamente para certificar-se de que eles não são expostos ao usuário acidentalmente. A regra [CA2118: revisar uso de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) pode ajudar com isso. Como alternativa, os métodos devem ter outra permissão que é exigida em vez de **UnmanagedCode** quando usá-los.  
  
 A exemplo a seguir mostra um **Cursor.Hide** método que encapsula o **ShowCursor** função na User32. dll.  
  
### <a name="code"></a>Código  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Avisos de design](../code-quality/design-warnings.md)