---
title: 'CA1040: Evitar interfaces vazias | Microsoft Docs'
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
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 50a32f619617662297b903b680276ce39854dbfd
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586989"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: evitar interfaces vazias
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1040: evitar interfaces vazias](https://docs.microsoft.com/visualstudio/code-quality/ca1040-avoid-empty-interfaces).

|||
|-|-|
|NomeDoTipo|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 A interface não declarar membros ou implementar duas ou mais interfaces.

## <a name="rule-description"></a>Descrição da Regra
 As interfaces definem os membros que fornecem um contrato de comportamento ou de uso. A funcionalidade descrita pela interface pode ser adotada por qualquer tipo, independentemente de onde o tipo seja exibido na hierarquia de herança. Um tipo implementa uma interface fornecendo implementações para os membros da interface. Uma interface vazia não define nenhum membro. Portanto, ele não define um contrato que pode ser implementado.

 Se seu design incluir vazio devem implementar interfaces tipos, você provavelmente está usando uma interface como um marcador ou uma maneira de identificar um grupo de tipos. Se essa identificação ocorrerá em tempo de execução, a maneira correta de fazer isso é usar um atributo personalizado. Use a presença ou ausência do atributo, ou as propriedades do atributo, para identificar os tipos de destino. Se a identificação deve ocorrer no tempo de compilação, é aceitável usar uma interface vazia.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova a interface ou adicionar membros a ela. Se a interface vazia estiver sendo usado para rotular um conjunto de tipos, substitua a interface com um atributo personalizado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, quando a interface é usada para identificar um conjunto de tipos em tempo de compilação.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma interface vazia.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]



