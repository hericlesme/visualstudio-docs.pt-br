---
title: 'CA2211: Os campos não constantes não devem estar visíveis | Microsoft Docs'
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
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d6ad55a49d335f5f776ba7b75f8006559e0eb38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587235"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: os campos não constantes não devem estar visíveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2211: os campos não constantes não devem ser visíveis](https://docs.microsoft.com/visualstudio/code-quality/ca2211-non-constant-fields-should-not-be-visible).

|||
|-|-|
|NomeDoTipo|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um campo estático público ou protegido não é constante nem somente leitura.

## <a name="rule-description"></a>Descrição da Regra
 Os campos estáticos que não são constantes nem somente leitura não são thread-safe. O acesso a esse campo deve ser cuidadosamente controlado e exige técnicas de programação avançadas para sincronizar o acesso ao objeto de classe. Como esses são difíceis de habilidades para aprender e mestre e testes de tal objeto apresenta seus próprios desafios, campos estáticos são melhor usados para armazenar dados que não são alterados. Essa regra se aplica às bibliotecas; aplicativos não devem expor todos os campos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, verifique o campo estático constantes ou somente leitura. Se isso não for possível, recrie o tipo para usar um mecanismo alternativo, como uma propriedade de thread-safe que gerencia o acesso thread-safe para o campo subjacente. Perceba que os problemas, como contenção de bloqueio e deadlocks podem afetar o desempenho e o comportamento da biblioteca.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se você estiver desenvolvendo um aplicativo e, portanto, têm controle total sobre o acesso ao tipo que contém o campo estático. Designers de bibliotecas não devem suprimir um aviso nessa regra; campos estáticos de não constante pode fazer usando a biblioteca difícil para os desenvolvedores para usar corretamente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



