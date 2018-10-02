---
title: 'CA1059: Os membros não devem expor certos tipos concretos | Microsoft Docs'
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
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 073d55a9a5ae6caa573a2c3db282aaa5e5ea4e57
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587248"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: os membros não devem expor determinados tipos concretos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1059: os membros não devem expor certos tipos concretos](https://docs.microsoft.com/visualstudio/code-quality/ca1059-members-should-not-expose-certain-concrete-types).

|||
|-|-|
|NomeDoTipo|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um membro visível externamente é um determinado tipo concreto ou expõe determinados tipos concretos por meio de um de seus parâmetros ou valor de retorno. No momento, esta regra relata a exposição dos tipos concretos a seguir:

-   Um tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Um tipo concreto é um tipo que tem uma implementação completa e, por isso, uma instância pode ser criada. Para permitir o uso difundido do membro, substitua o tipo concreto a interface sugerida. Isso permite que o membro aceitar qualquer tipo que implementa a interface ou ser usado onde um tipo que implementa a interface é esperado.

 A tabela a seguir lista os tipos de concretos de destino e suas substituições sugeridas.

|Tipo concreto|Substituição|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Usando a interface separa o membro de uma implementação específica de uma fonte de dados XML.|

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o tipo concreto para a interface sugerida.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma mensagem da regra se a funcionalidade específica fornecida pelo tipo concreto é necessária.

## <a name="related-rules"></a>Regras relacionadas
 [CA1011: considere passar os tipos base como parâmetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



