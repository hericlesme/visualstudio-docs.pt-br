---
title: "Propriedades de relações do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: "20"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 011be65e453de8f9d8010b74670b4efdf7905d06
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-relationships"></a>Propriedades de relacionamentos de domínio
As propriedades na tabela a seguir estão associadas com uma relação de domínio. Para obter informações sobre as relações de domínio, consulte [compreensão de modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|O nível de acesso da relação de domínio (`public` ou `internal`).|`public`|  
|Atributos personalizados|Usado para adicionar atributos para a classe do código fonte que é gerada da relação de domínio.|\<Nenhum >|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) é gerado. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Tem um construtor personalizado|Se `True`, indica que um construtor personalizado é fornecido no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerado da relação de domínio (`none`, `abstract` ou `sealed`).|\<Nenhum >|  
|Permite duplicatas|Se `True`, links duplicados da relação de domínio pode ser criados entre os mesmos dois elementos.|`False`|  
|Relações de base|Se a relação de domínio for derivada, a relação de base da relação de domínio.|\<Nenhum >|  
|É a incorporação|Se `True`, a relação de domínio é um relacionamento de incorporação. Se `False`, a relação é uma relação de referência.|\<ambos >|  
|Nome|O nome da relação de domínio.|Nome atual|  
|Namespace|O namespace associado com a relação de domínio.|Namespace atual|  
|Observações|Anotações informais que estão associadas com a relação de domínio.|\<Nenhum >|  
|Descrição|A descrição que é usada para documentar código e é usada na interface de usuário do designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que é exibido no designer gerado para a relação de domínio.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda de F1 para o relacionamento de domínio.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)