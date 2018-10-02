---
title: 'CA2138: Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity | Microsoft Docs'
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
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 127f2cb0a6aec99b858c75c43a2ee6cbbb2c6e94
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "47587951"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: os métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2138: métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity](https://docs.microsoft.com/visualstudio/code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute).

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método de segurança transparente chama um método que é marcado com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é acionada em qualquer método transparente chamado diretamente no código nativo, por exemplo, usando um por meio de um P/Invoke (invocação de plataforma) chamar. Métodos de interoperabilidade P/Invoke e COM que são marcados com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> resultam em um LinkDemand que está sendo feito em relação ao método de chamada do atributo. Porque o código transparente de segurança não é possível atender a LinkDemands, o código também não é possível chamar métodos que são marcados com o atributo SuppressUnmanagedCodeSecurity ou métodos da classe que é marcado com o atributo SuppressUnmanagedCodeSecurity. O método irá falhar ou a demanda será convertida em uma demanda completa.

 As violações dessa regra resultam em uma <xref:System.MethodAccessException> no modelo de transparência de segurança de nível 2 e uma demanda completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> no modelo de transparência de nível 1.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova os <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> de atributos e marcar o método com o <xref:System.Security.SecurityCriticalAttribute> ou o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]



