---
title: "CA1411: Os métodos de registro não devem ser visíveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67a4d4124ac1aae99327fdcd757db546cb50adfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: os métodos de registro COM não devem estar visíveis
|||  
|-|-|  
|NomeDoTipo|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo é visível externamente.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um assembly é registrado com o modelo de objeto de componente (COM), são adicionadas entradas no registro para cada tipo visível em COM no assembly. Métodos que são marcados com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributos são chamados durante os processos e cancelamento de registro, respectivamente, para executar o código do usuário que é específico para o registro/cancelamento do registro desses tipos. Esse código não deve ser chamado fora desses processos.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a acessibilidade do método para `private` ou `internal` (`Friend` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois métodos que violam a regra.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1410: os métodos de registro COM devem ser correspondentes](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrando assemblies usando COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (Ferramenta de Registro de Assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)