---
title: "CA2102: Capturar exceções não CLSCompliant em manipuladores gerais | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords: CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c241766a38ffc172924516e70b86ebdc22e117e2
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: capturar exceções que não sejam CLSCompliant em manipuladores gerais
|||  
|-|-|  
|NomeDoTipo|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um membro em um assembly que não está marcado com o <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou está marcado como `RuntimeCompatibility(WrapNonExceptionThrows = false)` contém um bloco catch que manipula <xref:System.Exception?displayProperty=fullName> e não contém um bloco catch geral imediatamente seguinte. Essa regra ignora [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] assemblies.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um bloco catch que manipula <xref:System.Exception> captura todas as exceções compatíveis do Common Language Specification (CLS). No entanto, ele não captura exceções compatível com CLS não. Não-CLS podem ser geradas exceções compatíveis do código nativo ou do código gerenciado que foi gerado pelo Microsoft intermediário language (MSIL) Assembler. Observe que o c# e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compiladores não permitem CLS não compatível com exceções seja gerada e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não capturará exceções compatível não-CLS. Se for a intenção do bloco catch tratar todas as exceções, use a seguinte sintaxe de bloco catch geral.  
  
-   C#:`catch {}`  
  
-   C++: `catch(...) {}` ou`catch(Object^) {}`  
  
 Exceção sem tratamento não-CLS compatível se torna um problema de segurança quando as permissões concedidas anteriormente são removidas no bloco catch. Porque exceções compatível não-CLS não são detectadas, um método mal-intencionado que gera uma não-CLS exceção compatível foi executado com permissões elevadas.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra quando a intenção é capturar todas as exceções, substituir ou adicionar um bloco catch geral ou marcar o assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Se as permissões são removidas no bloco catch, duplicar a funcionalidade geral bloco catch. Se não for a intenção de lidar com todas as exceções, substitua o bloco catch que manipula <xref:System.Exception> com blocos catch que lidam com tipos de exceção específica.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o bloco try não contém quaisquer instruções que podem gerar uma exceção de conformidade não-CLS. Pois qualquer código nativo ou gerenciado pode gerar uma não-CLS exceção compatível, isso requer conhecimento de todo o código que pode ser executado em todos os caminhos de código dentro do bloco try. Observe que as exceções compatível com CLS não não são geradas pelo common language runtime.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma classe MSIL que lança uma exceção de conformidade não-CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que contém um bloco catch geral que satisfaz a regra.  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Compile os exemplos anteriores da seguinte maneira.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1031: não capturar tipos de exceção gerais](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exceções e tratamento de exceções](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe (IL Assembler)](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [Componentes de independência de linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)