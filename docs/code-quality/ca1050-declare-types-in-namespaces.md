---
title: 'CA1050: Declarar tipos em namespaces | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 297491e6f3bdaef2b0d460bfe37716f6cae0dbd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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