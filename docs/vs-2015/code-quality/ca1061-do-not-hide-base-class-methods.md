---
title: 'CA1061: Não ocultar métodos de classe base | Microsoft Docs'
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
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f018abbb864533e5c9d7b598638a4006a69ab2f3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586990"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: não ocultar métodos de classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1061: não ocultar métodos de classe base](https://docs.microsoft.com/visualstudio/code-quality/ca1061-do-not-hide-base-class-methods).

|||
|-|-|
|NomeDoTipo|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo derivado declara um método com o mesmo nome e com o mesmo número de parâmetros como um de seus métodos base; um ou mais dos parâmetros é um tipo base do parâmetro correspondente no método base; e quaisquer parâmetros restantes têm tipos que são idênticos aos parâmetros correspondentes no método base.

## <a name="rule-description"></a>Descrição da Regra
 Um método em um tipo base permanece oculto por um método nomeado identicamente em um tipo derivado quando a assinatura do parâmetro do método derivado difere somente pelos tipos que são mais fracos derivadas que os tipos correspondentes na assinatura do parâmetro do método base.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remover ou renomear o método ou altere a assinatura do parâmetro para que o método não oculta o método base.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que viola a regra.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]



