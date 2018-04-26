---
title: 'CA1040: evitar interfaces vazias'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0de7459427fae4ea21cf1465167defea6d1d274
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: evitar interfaces vazias
|||
|-|-|
|NomeDoTipo|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 A interface não declarar membros ou implementar duas ou mais interfaces.

## <a name="rule-description"></a>Descrição da Regra
 As interfaces definem os membros que fornecem um contrato de comportamento ou de uso. A funcionalidade descrita pela interface pode ser adotada por qualquer tipo, independentemente de onde o tipo seja exibido na hierarquia de herança. Um tipo implementa uma interface fornecendo implementações para os membros da interface. Uma interface vazia não definir nenhum membro. Portanto, ele não define um contrato que pode ser implementado.

 Se seu design inclui vazio interfaces tipos devem implementar, provavelmente você está usando uma interface como um marcador ou uma maneira de identificar um grupo de tipos. Se essa identificação ocorrerá em tempo de execução, a maneira correta de fazer isso é usar um atributo personalizado. Use a presença ou ausência do atributo ou as propriedades do atributo, para identificar os tipos de destino. Se a identificação deve ocorrer em tempo de compilação, é aceitável para usar uma interface vazia.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remover a interface ou adicionar membros a ela. Se a interface vazia está sendo usada para identificar um conjunto de tipos, substitua a interface com um atributo personalizado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a interface é usada para identificar um conjunto de tipos em tempo de compilação.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma interface vazia.

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]