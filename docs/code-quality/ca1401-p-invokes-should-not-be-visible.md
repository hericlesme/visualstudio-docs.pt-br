---
title: 'CA1401: P-invoca não deve ser visível'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2aaadb0570e47e5ef41614925c20f8dc30f1620
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900598"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes não deve estar visível
|||
|-|-|
|NomeDoTipo|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método público ou protegido em um tipo público tem o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (também implementado pelo `Declare` palavra-chave em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Descrição da Regra
 Métodos que são marcados com o <xref:System.Runtime.InteropServices.DllImportAttribute> atributo (ou os métodos que são definidos usando o `Declare` palavra-chave em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) usar serviços de invocação de plataforma para acessar código não gerenciado. Esses métodos não devem ser expostos. Mantendo esses métodos privadas ou internas, certifique-se de que a biblioteca não pode ser usada de violação de segurança, permitindo que os chamadores acessem as APIs não gerenciadas que não poderia chamar caso contrário.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o nível de acesso do método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir declara um método que viola essa regra.

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]