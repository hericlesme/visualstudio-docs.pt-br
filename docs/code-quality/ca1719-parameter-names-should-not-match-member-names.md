---
title: 'CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1174fa0533519b551e237c685f0a6fe67661752a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915330"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro
|||
|-|-|
|NomeDoTipo|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um membro visível externamente corresponde, em uma comparação de maiusculas e minúsculas, o nome de um dos seus parâmetros.

## <a name="rule-description"></a>Descrição da Regra
 Um nome de parâmetro deve informar o significado de um parâmetro e um nome de membro deve informar o significado de um membro. Seria um design raro se eles fossem iguais. A nomenclatura de um parâmetro com o mesmo nome do membro não é intuitiva e dificulta o uso da biblioteca.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Selecione um nome de parâmetro que não coincide com o nome do membro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para novos desenvolvimentos, nenhum conhecidos situações ocorrer onde você deve suprimir um aviso dessa regra. Para bibliotecas de envio, você talvez precise suprimir um aviso dessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)