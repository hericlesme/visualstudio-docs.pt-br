---
title: 'CA1059: os membros não devem expor determinados tipos concretos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c872685445dddaf55efc8c5880b053c865ff2351
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898161"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: os membros não devem expor determinados tipos concretos
|||
|-|-|
|NomeDoTipo|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um membro visível externamente é um determinado tipo concreto ou expõe certos tipos concretos por meio de um de seus parâmetros ou valor de retorno. No momento, esta regra relata exposição dos seguintes tipos concretos:

-   Um tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Um tipo concreto é um tipo que tem uma implementação completa e, por isso, uma instância pode ser criada. Para permitir que o amplo uso do membro, substitua o tipo concreto com a interface sugerida. Isso permite que o membro aceitar qualquer tipo que implementa a interface ou ser usado onde um tipo que implementa a interface é esperado.

 A tabela a seguir lista os tipos concretos destino e suas substituições sugeridas.

|Tipo concreto|Substituição|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Usando a interface separa o membro de uma implementação específica de uma fonte de dados XML.|

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o tipo concreto para a interface sugerida.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma mensagem dessa regra se a funcionalidade específica fornecida pelo tipo concreto é necessária.

## <a name="related-rules"></a>Regras relacionadas
 [CA1011: considere passar os tipos base como parâmetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)