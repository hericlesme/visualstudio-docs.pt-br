---
title: 'CA1050: declarar tipos em namespaces'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 174f30b8f4e58d7289b93cd9f5a8a8253c7a4fba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: declarar tipos em namespaces
|||
|-|-|
|NomeDoTipo|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido está definido fora do escopo de um namespace nomeado.

## <a name="rule-description"></a>Descrição da Regra
 Os tipos são declarados nos namespaces para evitar conflitos de nome e como uma maneira de organizar tipos relacionados em uma hierarquia de objetos. Tipos que estão fora de qualquer namespace nomeada estão em um namespace global não pode ser referenciado no código.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, coloque o tipo em um namespace.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Embora você nunca tiver que suprimir um aviso dessa regra, é seguro fazer isso quando o assembly nunca será usado junto com outros assemblies.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma biblioteca que tenha um tipo declarado incorretamente fora de um namespace e um tipo que tem o mesmo nome declarado em um namespace.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir usa a biblioteca que foi definida anteriormente. Observe que o tipo que é declarado fora de um namespace é criado quando o nome `Test` não está qualificado por um namespace. Observe também que, para acessar o `Test` digite `Goodspace`, o nome do namespace é necessário.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]