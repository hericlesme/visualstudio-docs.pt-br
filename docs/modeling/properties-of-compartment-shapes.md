---
title: Propriedades de formas de compartimento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords: Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 007e1a6468429212ba7d1833157a4c9a2e771652
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
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
|Atributos personalizados|Usado para adicionar atributos para a classe de código fonte que é gerada a partir dessa forma do compartimento|\<Nenhum >|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir da forma de compartimento (`none`, `abstract` ou `sealed`).|Nenhum|  
|Forma do compartimento de base|A classe base dessa forma.|(nenhum)|  
|Nome|O nome dessa forma.|Nome atual|  
|Namespace|O namespace que é associado a esta forma.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixo, variável ou nenhum). Se for resolvido, em seguida, o valor da `Fixed Tooltip Text` propriedade é usada como a dica de ferramenta; se a variável, em seguida, a dica de ferramenta é definida no código personalizado.|nenhum|  
|Observações|Anotações informais que estão associadas esta forma.|\<Nenhum >|  
|Altura inicial|A altura inicial dessa forma, em polegadas. Para formas de compartimento, essa é a altura da seção de cabeçalho, somente e ele não pode ser redimensionado.|1|  
|Largura inicial|A largura inicial dessa forma, em polegadas.|1.5|  
|Cor de preenchimento exposto como propriedade<br /><br /> Modo de gradação de preenchimento exposto<br /><br /> Exposto a cor do contorno como propriedade<br /><br /> Exposto estilo do tracejado da estrutura de tópicos como propriedade<br /><br /> Exposto a espessura da estrutura de tópicos como propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário pode definir a propriedade declarada de uma forma. Para definir isso, a definição de forma de mouse e clique em **adicionar expostos**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta forma.|\<Nenhum >|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para esta forma.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)