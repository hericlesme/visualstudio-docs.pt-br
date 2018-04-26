---
title: 'CA2121: os construtores estáticos devem ser privados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f6eef1097565090fd1b9be572f9a33afed9afed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: os construtores estáticos devem ser privados
|||
|-|-|
|NomeDoTipo|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo tem um construtor estático não é privado.

## <a name="rule-description"></a>Descrição da Regra
 Um construtor estático, também conhecido como um construtor de classe é usado para inicializar um tipo. O sistema chama o construtor estático antes que a primeira instância do tipo seja criada ou que outros membros estáticos sejam referenciados. O usuário não tem controle sobre quando o construtor estático é chamado. Se não for privado, um construtor estático poderá ser chamado por um código diferente do sistema. Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado.

 Essa regra é aplicada, os compiladores c# e Visual Basic.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Violações geralmente são causadas por uma das seguintes ações:

-   Definido um construtor estático para o tipo e não faz privada.

-   O compilador de linguagem de programação adicionado um construtor estático padrão para seu tipo e não faz privada.

 Para corrigir o primeiro tipo de violação, torne o construtor estático privado. Para corrigir o segundo tipo, adicione um construtor estático privado para o seu tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima estas violações. Se o projeto de software requer uma chamada explícita para um construtor estático, é provável que o projeto contém falhas graves e deve ser revisado.