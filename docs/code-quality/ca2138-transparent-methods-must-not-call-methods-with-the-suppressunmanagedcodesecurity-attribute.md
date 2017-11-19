---
title: "CA2138: Os métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf17c69673649ac1f3af64bafcb718e8c84eb213
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: os métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity
|||  
|-|-|  
|NomeDoTipo|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método transparente de segurança chama um método marcado com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra é acionado em qualquer método transparente que chama diretamente no código nativo, por exemplo, usando um por meio de um P/Invoke (invocação de plataforma) chamar. P/Invoke e COM métodos de interoperabilidade que são marcados com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo resultam em um LinkDemand sendo feito com o método de chamada. Porque o código transparente de segurança não pode atender a LinkDemands, o código também não é possível chamar métodos que são marcados com o atributo SuppressUnmanagedCodeSecurity ou métodos da classe que está marcado com o atributo SuppressUnmanagedCodeSecurity. Haverá falha no método ou a demanda será convertida em uma solicitação total.  
  
 Violações desta regra levam a um <xref:System.MethodAccessException> no modelo de transparência de segurança de nível 2 e uma solicitação total de <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> no modelo de transparência de nível 1.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> de atributos e marcar o método com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]