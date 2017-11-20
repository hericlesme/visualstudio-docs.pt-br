---
title: "Propriedades de Classes do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e9bed31caa63a12677e7b9798e6cf72524500c21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-classes"></a>Propriedades de classes de domínio
Classes de domínio têm as propriedades na tabela a seguir. Para obter informações sobre classes de domínio, consulte [compreensão de modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|O nível de acesso da classe de domínio (`public` ou `internal`).|`public`|  
|Atributos personalizados|Usado para adicionar atributos para a classe do código fonte que é gerada a partir dessa classe de domínio.|\<Nenhum >|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada da classe de domínio (`none`, `abstract` ou `sealed`).|`none`|  
|Classe base|Se essa classe de domínio é derivado, o nome da classe base.|\<Nenhum >|  
|Nome|O nome desta classe de domínio.|Nome atual|  
|Namespace|O namespace desta classe de domínio.|Namespace atual|  
|Observações|Anotações informais que estão associadas essa classe de domínio.|\<Nenhum >|  
|Descrição|A descrição é usada para a interface do usuário do designer gerado de documento.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta classe de domínio.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda de F1 para essa classe de domínio.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)