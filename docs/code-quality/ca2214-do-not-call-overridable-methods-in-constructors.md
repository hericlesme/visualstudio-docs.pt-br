---
title: 'CA2214: não chamar métodos substituíveis em construtores'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5ebcd4164f9db28d4cb1f150ee3a4bb21b21cde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: não chamar métodos substituíveis em construtores
|||
|-|-|
|NomeDoTipo|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 O construtor de um tipo sem lacre chama um método virtual definido em sua classe.

## <a name="rule-description"></a>Descrição da Regra
 Quando um método virtual é chamado, o tipo real que executa o método não está selecionado até o tempo de execução. Quando um construtor chama um método virtual, é possível que o construtor para a instância que invoca o método não foi executado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, não chame métodos virtuais do tipo de construtores do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. O construtor deve ser reformulado para eliminar a chamada para o método virtual.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o efeito de violam essa regra. O aplicativo de teste cria uma instância de `DerivedType`, que faz com que a sua classe base (`BadlyConstructedType`) construtor para executar. `BadlyConstructedType`do construtor incorretamente chama o método virtual `DoSomething`. Como mostra a saída, `DerivedType.DoSomething()` executa e faz portanto, antes de `DerivedType`do construtor é executado.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

 Este exemplo gerencia a seguinte saída.

 **Chamando um construtor base. ** 
 **DoSomething derivada é chamado - inicializado? Não**
**chamada derivado ctor.**