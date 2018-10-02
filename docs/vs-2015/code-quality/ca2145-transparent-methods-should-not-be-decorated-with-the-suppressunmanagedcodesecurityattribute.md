---
title: 'CA2145: Métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
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
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7dcb7d2596a03bc78eed7dc4c3a1455c91478b04
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "47587945"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: os métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2145: métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute).

|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente, um método marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> método ou um tipo que contém um método é marcado com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descrição da Regra
 Os métodos decorados com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo têm um LinkDemand implícito colocado em qualquer método que o chama. Este LinkDemand requer que o código de chamada seja crítico de segurança. A marcação do método que usa SuppressUnmanagedCodeSecurity com o <xref:System.Security.SecurityCriticalAttribute> atributo torna esse requisito mais óbvio para chamadores do método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, marque o método ou tipo com o <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Comentários



