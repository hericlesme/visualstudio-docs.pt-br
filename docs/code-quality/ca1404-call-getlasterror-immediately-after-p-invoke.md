---
title: "CA1404: Chamar GetLastError imediatamente após chamar P | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 63cd84136861b80617285a5f7f03ff4767efddca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: chamar GetLastError logo depois de P/Invoke
|||  
|-|-|  
|NomeDoTipo|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 É feita uma chamada para o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> método ou o equivalente do Win32 `GetLastError` função e a chamada vem imediatamente antes não é uma plataforma de invocação de método.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Uma plataforma de chamar código não gerenciado do método acessa e é definido usando o `Declare` palavra-chave em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo. Em geral, após a falha, funções não gerenciadas chamam Win32 `SetLastError` função para definir um código de erro que é associado à falha. O chamador da função com falha chama o Win32 `GetLastError` função para recuperar o código de erro e determinar a causa da falha. O código de erro é mantido em uma base por thread e é substituído pela próxima chamada para `SetLastError`. Depois que uma chamada para uma plataforma com falha invocar o método, o código gerenciado pode recuperar o código de erro chamando o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> método. Como o código de erro pode ser substituído pelas chamadas internas de outros métodos de biblioteca de classes gerenciada, o `GetLastError` ou <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> método deve ser chamado imediatamente após a chamada de método de invocação de plataforma.  
  
 A regra ignora chamadas para os seguintes membros gerenciados quando eles ocorrem entre a chamada para a plataforma de invocação de método e a chamada para <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Esses membros não alteram o erro de código e são úteis para determinar o sucesso da plataforma de alguns invocam chamadas de método.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, mova a chamada para <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> para que fique imediatamente após a chamada para a plataforma de invocação de método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o código entre a plataforma de invocar a chamada de método e o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> chamada de método não é implicitamente ou explicitamente fazer com que o código de erro alterar.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que viola a regra e um método que satisfaz a regra.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1060: Mover P/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Os pontos de entrada P/Invoke devem existir](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes não devem ser visíveis](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: usar equivalentes gerenciados da API do Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)