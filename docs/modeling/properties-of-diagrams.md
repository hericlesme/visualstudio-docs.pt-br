---
title: Propriedades de diagramas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c00ec651510da84594c370e312112c50bc545606
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-diagrams"></a>Propriedades de diagramas
Você pode definir propriedades que especificam como os diagramas aparecerá no designer de gerado. Por exemplo, você pode especificar uma cor padrão para o texto no diagrama.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 A tabela a seguir lista as propriedades de diagramas.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor de preenchimento|A cor de preenchimento para o diagrama.|Branco|  
|Cor do texto|A cor do texto que é exibido no diagrama.|Preto|  
|Modificador de acesso|O modificador de acesso da classe (público ou interno).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe do código gerado.|\<none>|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir do diagrama (`none`, `abstract` ou `sealed`).|Nenhum|  
|Diagrama de base|A classe base do diagrama.|(nenhum)|  
|Nome|O nome do diagrama.|Nome atual|  
|Namespace|O namespace que é associado a este diagrama.|Namespace atual|  
|Classe representada|A classe de domínio raiz que este diagrama representa.|Classe raiz atual se aplicável|  
|Observações|Anotações informais que estão associadas esse elemento.|\<none>|  
|Cor de preenchimento expõe como propriedade|Se `True`, o usuário pode definir a cor de preenchimento do diagrama do designer gerado. Para configurar isso, clique com botão direito na forma de diagrama e clique em **Explosed adicionar**.|False|  
|Expõe a cor do texto como propriedade|Se `True`, o usuário pode definir a cor do texto do diagrama no designer de gerado. Para configurar isso, clique com botão direito na forma de diagrama e clique em **Explosed adicionar**.|False|  
|Descrição|A descrição é usada para documentar o designer gerado.|\<none>|  
|Nome de Exibição|O nome que será exibido no designer gerado para este diagrama.|\<none>|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar Ajuda F1 do diagrama.|\<none>|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)