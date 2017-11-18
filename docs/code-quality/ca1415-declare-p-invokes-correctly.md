---
title: 'CA1415: Declarar P-invoca corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9edc52bbc1cd05ed1a3a726dcfb49f26574ccc1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: declarar P/Invokes corretamente
|||  
|-|-|  
|NomeDoTipo|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Separação de não - se a P/Invoke que declara que o parâmetro não pode ser vista fora do assembly. Quebrar - se P/Invoke que declara o parâmetro pode ser visto fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Uma plataforma de invocar o método foi declarado incorretamente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Uma plataforma de chamar código não gerenciado do método acessa e é definido usando o `Declare` palavra-chave em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. No momento, esta regra de aparência para declarações de métodos que se destinam a funções do Win32 que tem um ponteiro para um parâmetro de estrutura OVERLAPPED de invocação de plataforma e o parâmetro gerenciado correspondente não é um ponteiro para um <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estrutura.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, declare corretamente a plataforma de invocação de método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra os métodos que violam a regra e atendem à regra de invocação de plataforma.  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)