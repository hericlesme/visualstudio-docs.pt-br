---
title: 'Ca2121: os Construtores estáticos devem ser privados | Microsoft Docs'
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
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b7052a25df5e736276b458247eb625ab584d473
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587129"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: os construtores estáticos devem ser privados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [ca2121 os: construtores estáticos devem ser privados](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private).

|||
|-|-|
|NomeDoTipo|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo tem um construtor estático que não é privado.

## <a name="rule-description"></a>Descrição da Regra
 Um construtor estático, também conhecido como um construtor de classe é usado para inicializar um tipo. O sistema chama o construtor estático antes que a primeira instância do tipo seja criada ou que outros membros estáticos sejam referenciados. O usuário não tem controle sobre quando o construtor estático é chamado. Se não for privado, um construtor estático poderá ser chamado por um código diferente do sistema. Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado.

 Essa regra é imposta pelos compiladores c# e Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Violações normalmente são causadas por uma das seguintes ações:

-   Definido um construtor estático para o seu tipo e não faz privada.

-   O compilador de linguagem de programação adicionado um construtor estático padrão para seu tipo e não faz privada.

 Para corrigir o primeiro tipo de violação, faça seu construtor estático privado. Para corrigir o segundo tipo, adicione um construtor estático privado para seu tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima essas violações. Se o projeto de software requer uma chamada explícita para um construtor estático, é provável que o design contém falha grave e deve ser revisado.



