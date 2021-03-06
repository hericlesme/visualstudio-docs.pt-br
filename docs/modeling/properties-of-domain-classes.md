---
title: Propriedades de classes de domínio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5d880ac873766c59adfa53e9e61a6ad13520c135
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949017"
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

- [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)