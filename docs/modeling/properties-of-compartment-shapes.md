---
title: Propriedades de formas de compartimento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e87af6c7b95fc05ab7e018f4b9adeb0ea9708868
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-compartment-shapes"></a>Propriedades de formas de compartimento
Formas de compartimento são uma das formas que você pode usar para exibir uma classe de domínio em uma linguagem específica de domínio. Você pode expandir e recolher os compartimentos.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formas de compartimento têm as propriedades que são listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Padrão expanda estado recolhido|Se `Expanded`, os compartimentos são mostrados na criação. Se `Collapsed`, eles não são.|Expandido|  
|Cor de preenchimento|A cor de preenchimento dessa forma.|Branco|  
|Preencher o modo de gradiente|O modo de preenchimento a gradação dessa forma.|Horizontal|  
|Geometry|A geometria dessa forma (retângulo ou um retângulo arredondado).|Retângulo|  
|Tem pontos de Conexão padrão|Se `True`, a forma usará superior, inferior, esquerda e pontos de conexão à direita no designer de gerado.|False|  
|Cabeçalho de compartimento único é visível|Se `False`e a forma tem um único compartimento, o cabeçalho do compartimento não está visível.|verdadeiro|  
|Cor do contorno|A cor do contorno dessa forma.|Preto|  
|Estilo do tracejado da estrutura de tópicos|O estilo de traço da estrutura de tópicos desta forma (sólido, tracejado, ponto, Traçoponto, Traçopontoponto, personalizado).|Sólido|  
|Espessura da estrutura de tópicos|A espessura da estrutura de tópicos dessa forma.|0.03125|  
|Cor do texto|A cor usada para decoradores de texto que estão associados esta forma.|Preto|  
|Modificador de acesso|O nível de acesso da forma compartimento (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código fonte que é gerada a partir dessa forma do compartimento|\<none>|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir da forma de compartimento (`none`, `abstract` ou `sealed`).|Nenhum|  
|Forma do compartimento de base|A classe base dessa forma.|(nenhum)|  
|Nome|O nome dessa forma.|Nome atual|  
|Namespace|O namespace que é associado a esta forma.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixo, variável ou nenhum). Se for resolvido, em seguida, o valor da `Fixed Tooltip Text` propriedade é usada como a dica de ferramenta; se a variável, em seguida, a dica de ferramenta é definida no código personalizado.|nenhum|  
|Observações|Anotações informais que estão associadas esta forma.|\<none>|  
|Altura inicial|A altura inicial dessa forma, em polegadas. Para formas de compartimento, essa é a altura da seção de cabeçalho, somente e ele não pode ser redimensionado.|1|  
|Largura inicial|A largura inicial dessa forma, em polegadas.|1.5|  
|Cor de preenchimento exposto como propriedade<br /><br /> Modo de gradação de preenchimento exposto<br /><br /> Exposto a cor do contorno como propriedade<br /><br /> Exposto estilo do tracejado da estrutura de tópicos como propriedade<br /><br /> Exposto a espessura da estrutura de tópicos como propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário pode definir a propriedade declarada de uma forma. Para definir isso, a definição de forma de mouse e clique em **adicionar expostos**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<none>|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta forma.|\<none>|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<none>|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para esta forma.|\<none>|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)