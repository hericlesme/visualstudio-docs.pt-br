---
title: "CA2123: As demandas de link de substituição devem ser idênticas à base | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e39d278588d8fbce5bc9a7ee77141a56341e8f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: as demandas de link de substituição devem ser idênticas à base
|||  
|-|-|  
|NomeDoTipo|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método público ou protegido em um tipo público substitui um método ou implementa uma interface e não tem o mesmo [demandas de Link](/dotnet/framework/misc/link-demands) como a interface ou método virtual.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra compara um método ao método de base, que é uma interface ou um método virtual em outro tipo e, em seguida, compara as exigências de vínculo em cada um. Uma violação será relatada se o método ou o método base tem uma demanda de link e o outro não.  
  
 Se esta regra for violada, um chamador mal-intencionado pode ignorar a demanda de link simplesmente chamando o método não seguro.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, aplica a mesma demanda de link para o método de substituir ou implementação. Se isso não for possível, marcar o método com uma solicitação total ou remova o atributo completamente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra várias violações desta regra.  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Demandas de link](/dotnet/framework/misc/link-demands)