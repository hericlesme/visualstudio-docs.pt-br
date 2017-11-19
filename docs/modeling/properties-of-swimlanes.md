---
title: Propriedades de raias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.swimlane
helpviewer_keywords: Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 1b8eacf8fdd74fc9fe0703dc50beb46a2442e939
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-swimlanes"></a>Propriedades de swimlanes
Você pode adicionar raias em um diagrama. Raias dividem um diagrama em áreas verticais ou horizontais. Você pode definir outras formas a ser exibida dentro raias. Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Raias têm as propriedades que são listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor de preenchimento de corpo|A cor de preenchimento para o corpo do swimlane.|Branco|  
|Cor de preenchimento de cabeçalho|A cor de preenchimento para o cabeçalho do swimlane.|Azul escuro|  
|Cor do separador|A cor da linha do separador.|LightGray|  
|Estilo de linha do separador|O estilo da linha do separador (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, ou `Custom`).|`Dash`|  
|Espessura do separador|A espessura da linha do separador em polegadas.|0.03125|  
|Cor do texto|A cor que é usada para decoradores de texto que estão associados este swimlane.|Preto|  
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código que é gerada neste swimlane.|\<Nenhum >|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir de swimlane (`none`, `abstract` ou `sealed`).|nenhum|  
|Swimlane base|A classe base desse swimlane.|(nenhum)|  
|Nome|O nome deste swimlane.|Nome atual|  
|Namespace|O namespace que é associado a este swimlane.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (`fixed`, `variable`, ou `none`). Se `fixed`, em seguida, o valor da `Fixed Tooltip Text` propriedade é usada; se `variable`, e em seguida, a dica de ferramenta é definida no código personalizado.|\<Nenhum >|  
|Observações|Anotações informais que estão associadas este swimlane.|\<Nenhum >|  
|Alinhamento|Alinhamento horizontal ou vertical.|Vertical|  
|Altura inicial|A altura inicial deste swimlane, em polegadas. Aplicável somente a raias horizontais.|0|  
|Largura inicial|A largura inicial deste swimlane, em polegadas. Aplicável somente a raias verticais.|0|  
|Expõe a cor do texto|Se `True`, o usuário pode definir a cor de um swimlane no designer de gerado. Para definir isso, clique com botão direito na forma de swimlane e clique em **adicionar expostos**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer para se referir a essa classe swimlane gerado.|\<Nenhum >|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para este swimlane.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)