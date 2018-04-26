---
title: 'CA2138: os métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: af499ac6299498f09ab7e6a6ff54b02dc4901815
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
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