---
title: "CA1405: Tipos de base de tipo visível COM devem ser visíveis no COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cceaee755af5269e266ca57e3644213e939c0ead
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: os tipos base de tipo visível em COM devem ser visíveis em COM
|||  
|-|-|  
|NomeDoTipo|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|DependsOnFix|  
  
## <a name="cause"></a>Causa  
 Um tipo de modelo de objeto de componente (COM) visível deriva de um tipo que não é visível de COM.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um tipo visível COM adiciona membros em uma nova versão, ele deve obedecer diretrizes rígidas para evitar que os clientes COM associados para a versão atual. Um tipo que é invisível para COM presume que não é necessário que seguem estas regras de controle de versão de COM ao adicionar novos membros. No entanto, se um visíveis no COM tipo deriva do tipo invisível COM e expõe uma interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> (o padrão), todos os membros públicos do tipo base (a menos que eles são especificamente marcados COM como invisíveis, qual seria redundante) são exposto a COM. Se o tipo base adiciona novos membros em uma versão posterior, podem interromper qualquer clientes COM qual associar a interface de classe do tipo derivado. Tipos visíveis no COM devem derivar somente a tipos visíveis no COM para reduzir a chance de clientes COM de quebra.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, verifique os tipos base visíveis no COM ou o tipo derivado COM invisível.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)