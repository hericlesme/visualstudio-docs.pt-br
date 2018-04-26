---
title: Propriedades de formas geométricas
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 54174dcb70440809eda9712d451c2b60fe8bb064
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-geometry-shapes"></a>Propriedades de formas geométricas
Você pode usar formas de geometria para especificar como as instâncias de classes de domínio são exibidas em uma linguagem específica de domínio. Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Formas de geometria têm as propriedades que são listadas na tabela a seguir.

|Propriedade|Descrição|Padrão|
|--------------|-----------------|-------------|
|Cor de preenchimento|A cor de preenchimento dessa forma.|Branco|
|Preencher o modo de gradiente|O modo de preenchimento a gradação dessa forma (Horizontal, Vertical, Diagonal para frente, Diagonal para trás ou nenhum).|Horizontal|
|Geometry|A geometria dessa forma (retângulo, retângulo arredondado, elipse ou círculo).|Retângulo|
|Tem pontos de Conexão padrão|Se `True`, a forma usará superior, inferior, esquerda e pontos de conexão à direita no designer de gerado.|False|
|Cor do contorno|A cor do contorno dessa forma.|Preto|
|Estilo do tracejado da estrutura de tópicos|O estilo de traço da estrutura de tópicos desta forma (sólido, tracejado, ponto, Traçoponto, Traçopontoponto ou personalizado).|Sólido|
|Espessura da estrutura de tópicos|A espessura da estrutura de tópicos dessa forma.|0.03125|
|Cor do texto|A cor que é usada para decoradores de texto que estão associados esta forma.|Preto|
|Modificador de acesso|O modificador de acesso da classe (público ou interno).|Público|
|Atributos personalizados|Usado para adicionar atributos para a classe do código fonte que é gerada para esta forma.|\<Nenhum >|
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerado de forma (`none`, `abstract` ou `sealed`).|nenhum|
|Forma de geometria de base|A classe base dessa forma.|(nenhum)|
|Nome|O nome dessa forma.|Nome atual|
|Namespace|O namespace que é associado a esta forma.|Namespace atual|
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixo, variável ou nenhum). Se for resolvido, em seguida, o valor da `Fixed Tooltip Text` propriedade é usada como a dica de ferramenta; se a variável, em seguida, a dica de ferramenta é definida no código personalizado.|Nenhum|
|Observações|Anotações informais que estão associadas esse elemento.|\<Nenhum >|
|Altura inicial|Altura inicial dessa forma, em polegadas.|1|
|Largura inicial|Largura inicial dessa forma, em polegadas.|1.5|
|Cor de preenchimento exposto como propriedade<br /><br /> Modo de gradação de preenchimento exposto<br /><br /> Exposto a cor do contorno como propriedade<br /><br /> Exposto estilo do tracejado da estrutura de tópicos como propriedade<br /><br /> Exposto a espessura da estrutura de tópicos como propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário pode definir a propriedade declarada de uma forma. Para definir isso, a definição de forma de mouse e clique em **adicionar expostos**.|False|
|Descrição|A descrição é usada para documentar o designer gerado.|\<Nenhum >|
|Nome de Exibição|O nome que será exibido no designer gerado para esta forma.|\<Nenhum >|
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para esta forma.|\<Nenhum >|

## <a name="see-also"></a>Consulte também

- [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)