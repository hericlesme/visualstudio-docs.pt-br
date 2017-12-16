---
title: "CA1408: Não usar AutoDual ClassInterfaceType | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47b872afd70a357938b8a9fd3fc7ecf7b180f77b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: não usar AutoDual ClassInterfaceType
|||  
|-|-|  
|NomeDoTipo|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo de modelo de objeto de componente (COM) visível é marcado com o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo definido como o `AutoDual` valor <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Tipos que usam uma interface dupla permitem que clientes sejam associados a um layout de interface específico. Todas as alterações feitas em uma versão futura do layout do tipo ou de qualquer tipo de base interromperão clientes COM associados à interface. Por padrão, se o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo não for especificado, uma interface somente de expedição é usada.  
  
 A menos que marcada caso contrário, todos os tipos de não-genéricos públicos são visíveis no COM; todos os tipos genéricos e confidenciais são visíveis para COM.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o valor da <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> de atributo para o `None` valor <xref:System.Runtime.InteropServices.ClassInterfaceType> e definir explicitamente a interface.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso dessa regra, a menos que você tiver certeza de que o layout do tipo e seus tipos base não será alterado em uma versão futura.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma classe que viola a regra e uma nova declaração de classe para usar uma interface explícita.  
  
 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1403: os tipos de layout automático não devem ser visíveis em COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: marcar interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## <a name="see-also"></a>Consulte também  
 [Qualificando tipos do .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)