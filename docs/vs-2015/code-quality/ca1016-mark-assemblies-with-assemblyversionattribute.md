---
title: 'CA1016: Marcar assemblies com AssemblyVersionAttribute | Microsoft Docs'
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
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 72e079f08eb04a68185800e77b815464045259bb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586971"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: marcar assemblies com AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1016: marcar assemblies com AssemblyVersionAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1016-mark-assemblies-with-assemblyversionattribute).

|||
|-|-|
|NomeDoTipo|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 O assembly não tem um número de versão.

## <a name="rule-description"></a>Descrição da Regra
 A identidade de um assembly é composta das seguintes informações:

-   Nome do assembly

-   Número de versão

-   Cultura

-   Chave pública (para assemblies fortemente nomeados).

 O [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usa o número de versão para identificar com exclusividade um assembly e associar a tipos em assemblies altamente nomeados. O número de versão é usado com a versão e a política do publicador. Por padrão, os aplicativos só são executados com a versão do assembly com que foram criados.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicionar um número de versão ao assembly usando o <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributo. Consulte o exemplo a seguir.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra para assemblies que são usados por terceiros ou em um ambiente de produção.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um assembly que tem o <xref:System.Reflection.AssemblyVersionAttribute> atributo aplicado.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Consulte também
 [Controle de versão do assembly](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [como: criar uma política de editor](http://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)



