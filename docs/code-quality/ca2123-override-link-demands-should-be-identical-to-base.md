---
title: 'CA2123: as demandas de link de substituição devem ser idênticas à base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 340b0e7deb12d4568a76d4871eabd49641926dcb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920356"
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
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines) [demandas de Link](/dotnet/framework/misc/link-demands)