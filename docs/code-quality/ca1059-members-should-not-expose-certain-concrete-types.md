---
title: "CA1059: Os membros não devem expor certos tipos concretos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5b8b4a50ce23a7ed50f2e608334f9b438a0b090
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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