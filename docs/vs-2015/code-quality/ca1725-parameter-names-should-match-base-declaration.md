---
title: 'CA1725: Os nomes de parâmetro devem corresponder à declaração base | Microsoft Docs'
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
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 20a7e5f0239d572ec1867ffdac80f116cfd8360a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587244"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: os nomes de parâmetro devem corresponder à declaração base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1725: os nomes de parâmetro devem corresponder à declaração base](https://docs.microsoft.com/visualstudio/code-quality/ca1725-parameter-names-should-match-base-declaration).

|||
|-|-|
|NomeDoTipo|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um parâmetro em uma substituição do método visível externamente não coincide com o nome do parâmetro em que a declaração do método de base ou o nome do parâmetro na declaração de interface do método.

## <a name="rule-description"></a>Descrição da Regra
 A nomenclatura consistente dos parâmetros em uma hierarquia de substituição aumenta a usabilidade das substituições de método. Um nome de parâmetro em um método derivado diferente do nome na declaração de base pode causar confusão em relação à possibilidade do método ser uma substituição do método de base ou de uma nova sobrecarga do método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, renomeie o parâmetro para corresponder à declaração base. A correção é uma alteração significativa para os métodos visíveis.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra, exceto para os métodos visíveis nas bibliotecas que foram enviados anteriormente.



