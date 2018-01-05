---
title: "CA2136: Os membros não devem ter anotações de transparência conflitantes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aad39e8b42a709aabc6321718a671510a5b686da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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