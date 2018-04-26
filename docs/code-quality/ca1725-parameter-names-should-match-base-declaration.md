---
title: 'CA1725: os nomes de parâmetro devem corresponder à declaração base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3564f3713dd24488e71703e902ae63f09b6aa74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: os nomes de parâmetro devem corresponder à declaração base
|||
|-|-|
|NomeDoTipo|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um parâmetro em uma substituição de método externamente visível não coincide com o nome do parâmetro na declaração do método base, ou o nome do parâmetro na declaração do método de interface.

## <a name="rule-description"></a>Descrição da Regra
 A nomenclatura consistente dos parâmetros em uma hierarquia de substituição aumenta a usabilidade das substituições de método. Um nome de parâmetro em um método derivado diferente do nome na declaração de base pode causar confusão em relação à possibilidade do método ser uma substituição do método de base ou de uma nova sobrecarga do método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, renomeie o parâmetro para corresponder a declaração base. A correção é uma alteração significativa para os métodos com visível.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso dessa regra, exceto os métodos visíveis nas bibliotecas que tiveram enviado anteriormente.