---
title: 'CA1017: Marcar assemblies com ComVisibleAttribute | Microsoft Docs'
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
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 931965388bd48ade5a0c9f5045b0399bed40a207
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587139"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: marcar assemblies com ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1017: marcar assemblies com ComVisibleAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1017-mark-assemblies-with-comvisibleattribute).

|||
|-|-|
|NomeDoTipo|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um assembly não tem o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo aplicado a ele.

## <a name="rule-description"></a>Descrição da Regra
 O <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina como os clientes COM acessam código gerenciado. Um bom design determina que os assemblies indiquem explicitamente a visibilidade de COM. Visibilidade de COM pode ser definida para um assembly inteiro e, em seguida, substituída por tipos individuais e membros de tipo. Se o atributo não estiver presente, o conteúdo do assembly é visível para os clientes COM.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione o atributo ao assembly. Se você não quiser que o assembly seja visível para os clientes COM, aplique o atributo e definir seu valor como `false`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Se você quiser que o assembly esteja visível, aplique o atributo e definir seu valor como `true`.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um assembly que tem o <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo aplicado para impedir que ele fique visível para os clientes COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Consulte também
 [Interoperação com código não gerenciado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualificando tipos do .NET para interoperação](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



