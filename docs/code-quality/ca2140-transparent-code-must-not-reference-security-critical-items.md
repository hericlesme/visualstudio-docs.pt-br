---
title: 'CA2140: o código transparente não deve fazer referência a itens críticos de segurança'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02de86564f6d7754b3c9db86d93577c374a72e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918430"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: o código transparente não deve fazer referência a itens críticos de segurança
|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente:

-   manipula um tipo de exceção de segurança crítica de segurança

-   tem um parâmetro que está marcado como um tipo crítico de segurança

-   tem um parâmetro genérico com um restrições críticas de segurança

-   tem uma variável local de um tipo crítico de segurança

-   faz referência a um tipo que está marcado como segurança crítico

-   chama um método que está marcado como segurança crítico

-   faz referência a um campo que está marcado como segurança crítico

-   Retorna um tipo que está marcado como segurança crítico

## <a name="rule-description"></a>Descrição da Regra
 Um elemento de código que está marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo é crítico de segurança. Um método transparente não pode usar um elemento crítico para segurança. Se um tipo transparente tenta usar um tipo crítico de segurança uma <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , ou <xref:System.FieldAccessException> é gerado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, siga um destes procedimentos:

-   Marcar o elemento de código que usa o código de segurança crítica com o <xref:System.Security.SecurityCriticalAttribute> atributo

     \- ou -

-   Remover o <xref:System.Security.SecurityCriticalAttribute> atributos dos elementos de código que são marcados como segurança crítica e em vez disso, marcá-los com o <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityTransparentAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 Nos exemplos a seguir, um método transparente tenta fazer referência a uma coleção genérica críticos de segurança, um campo crítico de segurança e um método de segurança crítica.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.Security.SecurityTransparentAttribute><xref:System.Security.SecurityCriticalAttribute><xref:System.Security.SecurityTransparentAttribute><xref:System.Security.SecurityTreatAsSafeAttribute><xref:System.Security?displayProperty=fullName>