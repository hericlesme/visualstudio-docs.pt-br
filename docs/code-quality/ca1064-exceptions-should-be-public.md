---
title: "CA1064: Exceções devem ser públicas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd39b4655f4a1bc98e408655e86fa1068820c9f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: as exceções devem ser públicas
|||  
|-|-|  
|NomeDoTipo|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Uma exceção não público deriva diretamente <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Uma exceção interna só é visível dentro de seu próprio escopo interno. Depois que a exceção falha fora do escopo interno, somente a exceção de base pode ser usada para capturar a exceção. Se a exceção interna for herdada de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, o código externo não terá informações suficientes para saber o que fazer com a exceção.  
  
 Mas, se o código tem uma exceção pública que é usada posteriormente como base para uma exceção interna, é razoável pressupor que o código adicional-out será capaz de fazer algo inteligente com a exceção de base. A exceção pública terão mais informações que é fornecido por T:System.Exception, T:System.SystemException ou T:System.ApplicationException.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Verifique a exceção pública ou derivar a exceção interna de uma exceção de pública que não seja <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima uma mensagem dessa regra, se você tiver certeza em todos os casos que a exceção privada será capturada dentro de seu próprio escopo interno.  
  
## <a name="example"></a>Exemplo  
 Esta regra é disparada no primeiro método de exemplo, FirstCustomException porque a classe de exceção deriva diretamente da exceção e é interna. A regra não funciona na classe SecondCustomException, porque embora a classe também deriva diretamente da exceção, a classe está declarado como pública. A classe de terceiros também não acionar a regra porque ele não deriva diretamente da <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, ou <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]