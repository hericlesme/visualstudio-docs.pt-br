---
title: "CA1410: Os métodos de registro devem ser correspondidos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c6191aff1433d050c1f7b50097c88d1d3cf2a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: os métodos de registro COM devem ser correspondentes
|||  
|-|-|  
|NomeDoTipo|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo declara um método marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> de atributo, mas não declara um método marcado com o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo, ou vice-versa.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Para clientes do modelo de objeto de componente (COM) para criar um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipo, o tipo deve primeiro ser registrado. Se estiver disponível, um método marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atributo é chamado durante o processo de registro para executar o código especificado pelo usuário. Um método correspondente que é marcado com o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributo é chamado durante o processo de cancelamento de registro para reverter as operações do método de registro.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione o método de cancelamento de registro ou registro correspondente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra. O código comentado mostra a correção para a violação.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1411: os métodos de registro COM não devem estar visíveis](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registrando assemblies usando COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (Ferramenta de Registro de Assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)