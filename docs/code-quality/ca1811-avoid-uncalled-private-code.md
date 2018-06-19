---
title: 'CA1811: evitar código privado não chamado'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f37ef9cdc76b86d3ad3c18489f63fb5c340aa6a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918458"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: evitar código privado não chamado
|||
|-|-|
|NomeDoTipo|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Membro privado ou interno (nível de assembly) não tem chamadores no assembly, não é invocado pelo common language runtime e não é invocado por um representante. Os seguintes membros não são verificados por essa regra:

-   Membros de interface explícita.

-   Construtores estáticos.

-   Construtores de serialização.

-   Os métodos marcados como <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Membros que são substituições.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra pode relatar falsos positivos se ocorrerem de pontos de entrada que atualmente não são identificados pela lógica de regra. Além disso, um compilador pode emitir código noncallable em um assembly.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova o código noncallable ou adicione o código que chama.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: examinar parâmetros não usados](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)