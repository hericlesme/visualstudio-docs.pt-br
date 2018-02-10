---
title: Propriedades de raias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 39bb6be4146cf7e9e163b6da5ada6f447a930bc8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-swimlanes"></a>Propriedades de swimlanes
Você pode adicionar raias em um diagrama. Raias dividem um diagrama em áreas verticais ou horizontais. Você pode definir outras formas a ser exibida dentro raias. Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Raias têm as propriedades que são listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor de preenchimento de corpo|A cor de preenchimento para o corpo do swimlane.|Branco|  
|Cor de preenchimento de cabeçalho|A cor de preenchimento para o cabeçalho do swimlane.|DarkGray|  
|Cor do separador|A cor da linha do separador.|LightGray|  
|Estilo de linha do separador|O estilo da linha do separador (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, ou `Custom`).|`Dash`|  
|Espessura do separador|A espessura da linha do separador em polegadas.|0.03125|  
|Cor do texto|A cor que é usada para decoradores de texto que estão associados este swimlane.|Preto|  
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código que é gerada neste swimlane.|\<none>|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir de swimlane (`none`, `abstract` ou `sealed`).|nenhum|  
|Swimlane base|A classe base desse swimlane.|(nenhum)|  
|Nome|O nome deste swimlane.|Nome atual|  
|Namespace|O namespace que é associado a este swimlane.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (`fixed`, `variable`, ou `none`). Se `fixed`, em seguida, o valor da `Fixed Tooltip Text` propriedade é usada; se `variable`, e em seguida, a dica de ferramenta é definida no código personalizado.|\<none>|  
|Observações|Anotações informais que estão associadas este swimlane.|\<none>|  
|Alinhamento|Alinhamento horizontal ou vertical.|Vertical|  
|Altura inicial|A altura inicial deste swimlane, em polegadas. Aplicável somente a raias horizontais.|0|  
|Largura inicial|A largura inicial deste swimlane, em polegadas. Aplicável somente a raias verticais.|0|  
|Expõe a cor do texto|Se `True`, o usuário pode definir a cor de um swimlane no designer de gerado. Para definir isso, clique com botão direito na forma de swimlane e clique em **adicionar expostos**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<none>|  
|Nome de Exibição|O nome que será exibido no designer para se referir a essa classe swimlane gerado.|\<none>|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<none>|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para este swimlane.|\<none>|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)