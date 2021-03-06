---
title: 'CA2214: Não chamar métodos substituíveis em construtores | Microsoft Docs'
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
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8e813488e5e935c54a50238c3c993c6efcbf232c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587230"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: não chamar métodos substituíveis em construtores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2214: não chamar métodos substituíveis em construtores](https://docs.microsoft.com/visualstudio/code-quality/ca2214-do-not-call-overridable-methods-in-constructors).

|||
|-|-|
|NomeDoTipo|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 O construtor de um tipo sem lacre chama um método virtual definido na sua classe.

## <a name="rule-description"></a>Descrição da Regra
 Quando um método virtual é chamado, o tipo real que executa o método não está selecionado até o tempo de execução. Quando um construtor chama um método virtual, é possível que o construtor para a instância que invoca o método não executado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, não chame métodos virtuais de um tipo de dentro de construtores do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. O construtor deve ser reformulado para eliminar a chamada para o método virtual.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra o efeito de violação dessa regra. O aplicativo de teste cria uma instância de `DerivedType`, que faz com que sua classe base (`BadlyConstructedType`) construtor ser executado. `BadlyConstructedType`do construtor incorretamente chama o método virtual `DoSomething`. Como mostra a saída, `DerivedType.DoSomething()` executa e faz, portanto, antes de `DerivedType`do construtor é executado.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Este exemplo gerencia a seguinte saída.

 **Chamando o construtor base. ** 
 **DoSomething derivado é chamado - inicializado? Não**
**chamada derivado ctor.**



