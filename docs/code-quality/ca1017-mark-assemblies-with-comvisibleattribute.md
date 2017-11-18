---
title: 'CA1017: Marcar assemblies com ComVisibleAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e4c76efff009c85f9d607611d92d53cad5d2759
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: marcar assemblies com ComVisibleAttribute
|||  
|-|-|  
|NomeDoTipo|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um assembly não tem o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo aplicado a ele.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina como os clientes COM acessam a código gerenciado. Um bom design determina que os assemblies indiquem explicitamente a visibilidade de COM. Visibilidade COM pode ser definida para um conjunto inteiro e, em seguida, substituída para individuais tipos e membros de tipo. Se o atributo não estiver presente, o conteúdo do assembly é visível para clientes COM.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione o atributo para o assembly. Se você não quiser que o assembly seja visível para clientes COM, aplique o atributo e defina seu valor como `false`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Se você quiser que o assembly esteja visível, aplique o atributo e defina seu valor como `true`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um assembly que tem o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo aplicado para impedir que ele seja visível para clientes COM.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)   
 [Qualificando tipos .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)