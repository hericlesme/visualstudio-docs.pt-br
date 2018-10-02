---
title: 'CA2132: Os construtores padrão devem ser pelo menos críticos como construtores padrão do tipo de base | Microsoft Docs'
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
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ecf78792e18df4956fa0147754879fb2e80648bc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587334"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: os construtores padrão devem ser pelo menos críticos como construtores padrão do tipo base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2132: construtores padrão devem ser pelo menos críticos como construtores padrão do tipo base](https://docs.microsoft.com/visualstudio/code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors).

|||
|-|-|
|NomeDoTipo|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

> [!NOTE]
>  Esse aviso só será aplicado ao código que está executando o CoreCLR (a versão do CLR que é específico para aplicativos Web do Silverlight).

## <a name="cause"></a>Causa
 O atributo de transparência do construtor padrão de uma classe derivada não é tão crítico quanto a transparência da classe base.

## <a name="rule-description"></a>Descrição da Regra
 Tipos e membros que têm o <xref:System.Security.SecurityCriticalAttribute> não pode ser usado pelo código do aplicativo do Silverlight. Os tipos de segurança crítica e os membros só podem ser usados por código confiável no .NET Framework para a biblioteca de classes do Silverlight. Como uma construção pública ou protegida em uma classe derivada deve ter a mesma transparência maior que sua classe base, uma classe em um aplicativo não pode ser derivada de uma classe marcada como SecurityCritical.

 Para o código de plataforma do CoreCLR, se um tipo base tem um construtor público ou protegido padrão não transparente, em seguida, o tipo derivado deve obedecer as regras de herança do construtor padrão. O tipo derivado também deve ter um construtor padrão e esse construtor deve ser pelo menos construtor crítica do padrão do tipo base.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir a violação, remova o tipo ou não derivam de tipo não transparente de segurança.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima avisos dessa regra. As violações dessa regra pelo código do aplicativo resultará no CoreCLR se recusando a carregar o tipo com um <xref:System.TypeLoadException>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Comentários



