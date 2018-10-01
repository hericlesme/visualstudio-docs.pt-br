---
title: Propriedades de Classes de domínio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d5ea3d5cad378a476c9080cd56143b1600b7b4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464746"
---
# <a name="properties-of-domain-classes"></a>Propriedades de classes de domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [propriedades de Classes de domínio](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-classes).  
  
Classes de domínio têm as propriedades na tabela a seguir. Para obter informações sobre classes de domínio, consulte [Noções básicas sobre modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|O nível de acesso da classe de domínio (`public` ou `internal`).|`public`|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código de origem que é gerada a partir dessa classe de domínio.|\<Nenhum >|  
|Gera dupla derivado|Se `True`, serão geradas uma classe base e uma classe parcial (para dar suporte à personalização por meio de substituições). Para obter mais informações, consulte [substituindo e estendendo as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Tem um construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herança|Descreve o tipo de herança da classe de código de origem que é gerado a partir da classe de domínio (`none`, `abstract` ou `sealed`).|`none`|  
|Classe base|Se essa classe de domínio é derivada, o nome da classe base.|\<Nenhum >|  
|Nome|O nome dessa classe de domínio.|Nome atual|  
|Namespace|O namespace da classe de domínio.|Namespace atual|  
|Observações|Observações informais associadas essa classe de domínio.|\<Nenhum >|  
|Descrição|A descrição é usada para documentar a interface do usuário do designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para essa classe de domínio.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda de F1 para esta classe de domínio.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



