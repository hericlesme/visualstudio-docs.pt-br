---
title: 'CA2208: instanciar exceções de argumento corretamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc4a13746182136e10cb550bb7235a8bad2528fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919121"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: instanciar exceções de argumento corretamente
|||
|-|-|
|NomeDoTipo|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Possíveis causas incluem as seguintes situações:

-   É feita uma chamada para o construtor (sem parâmetros) padrão de um tipo de exceção ou derivado de <xref:System.ArgumentException>.

-   Um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção ou derivado de <xref:System.ArgumentException>.

## <a name="rule-description"></a>Descrição da Regra
 Em vez de chamar o construtor padrão, chame uma das sobrecargas de construtor que permite que uma mensagem de exceção mais significativa ser fornecido. A mensagem de exceção deve direcionar o desenvolvedor e explicam claramente a condição de erro e como corrigir ou evitar a exceção.

 As assinaturas dos construtores de cadeia de caracteres de uma e duas de <xref:System.ArgumentException> e seus tipos derivados não são consistentes com relação ao `message` e `paramName` parâmetros. Verifique se que esses construtores são chamados com os argumentos de cadeia de caracteres correta. As assinaturas são da seguinte maneira:

 <xref:System.ArgumentException>(cadeia de caracteres `message`)

 <xref:System.ArgumentException>(cadeia de caracteres `message`, cadeia de caracteres `paramName`)

 <xref:System.ArgumentNullException>(cadeia de caracteres `paramName`)

 <xref:System.ArgumentNullException>(cadeia de caracteres `paramName`, cadeia de caracteres `message`)

 <xref:System.ArgumentOutOfRangeException>(cadeia de caracteres `paramName`)

 <xref:System.ArgumentOutOfRangeException>(cadeia de caracteres `paramName`, cadeia de caracteres `message`)

 <xref:System.DuplicateWaitObjectException>(cadeia de caracteres `parameterName`)

 <xref:System.DuplicateWaitObjectException>(cadeia de caracteres `parameterName`, cadeia de caracteres `message`)

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, chamar um construtor que recebe uma mensagem, um nome de parâmetro ou ambos e verifique se os argumentos são adequados para o tipo de <xref:System.ArgumentException> que está sendo chamado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra somente se um construtor com parâmetros é chamado com os argumentos de cadeia de caracteres correta.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um construtor que incorretamente cria uma instância do tipo ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação acima alternando os argumentos de construtor.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]