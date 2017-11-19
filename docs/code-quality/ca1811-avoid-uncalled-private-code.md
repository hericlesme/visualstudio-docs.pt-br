---
title: "CA1811: Evitar código privado não chamado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fc7bac9804c42cb7910df6b6d89ad766b09ee0d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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