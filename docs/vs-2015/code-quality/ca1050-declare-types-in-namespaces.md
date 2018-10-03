---
title: 'CA1050: Declarar tipos em namespaces | Microsoft Docs'
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
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ef0559cc727e7ffd667ee72ebe241a958fa57450
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587010"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: declarar tipos em namespaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1050: declarar tipos em namespaces](https://docs.microsoft.com/visualstudio/code-quality/ca1050-declare-types-in-namespaces).

|||
|-|-|
|NomeDoTipo|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido é definido fora do escopo de um namespace nomeado.

## <a name="rule-description"></a>Descrição da Regra
 Tipos são declarados em namespaces para evitar colisões de nome e como uma forma de organizar tipos relacionados em uma hierarquia de objetos. Tipos que estão fora de qualquer namespace nomeado estão em um namespace global que não pode ser referenciado no código.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, coloque o tipo em um namespace.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Embora você nunca precisará suprimir um aviso nessa regra, é seguro fazer isso quando o assembly nunca será usado em conjunto com outros assemblies.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma biblioteca que tenha um tipo declarado incorretamente fora de um namespace e um tipo que tem o mesmo nome declarado em um namespace.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir usa a biblioteca que foi definida anteriormente. Observe que o tipo que é declarado fora de um namespace é criado quando o nome `Test` não são qualificados por um namespace. Observe também que, para acessar o `Test` digitar `Goodspace`, o nome do namespace é necessário.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]



