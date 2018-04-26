---
title: 'CA2136: os membros não devem ter anotações de transparência conflitantes'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afcfe25a9ff4541331ddfc35ebe86bbf884ef02e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: os membros não devem ter anotações de transparência conflitantes
|||
|-|-|
|NomeDoTipo|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Esta regra é disparada quando um membro de tipo está marcado com um <xref:System.Security> atributo de segurança que tem uma transparência diferente que o atributo de segurança de um contêiner do membro.

## <a name="rule-description"></a>Descrição da Regra
 Os atributos de transparência são aplicados com base nos elementos de código de escopo maior a elementos de escopo menor. Os atributos de transparência dos elementos de código com escopo maior têm precedência sobre atributos de transparência dos elementos de código contidos no primeiro elemento. Por exemplo, uma classe marcada com o <xref:System.Security.SecurityCriticalAttribute> atributo não pode conter um método marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir essa violação, remova o atributo de segurança do elemento de código que tem o menor escopo ou alterar seu atributo para ser o mesmo que o elemento de código que contém.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima avisos dessa regra.

## <a name="example"></a>Exemplo
 No exemplo a seguir, um método é marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> atributo e é um membro de uma classe marcada com o <xref:System.Security.SecurityCriticalAttribute> atributo. O atributo de segurança de segurança deve ser removido.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]