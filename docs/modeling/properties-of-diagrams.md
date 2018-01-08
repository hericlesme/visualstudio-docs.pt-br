---
title: Propriedades de diagramas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords: Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: "25"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4c1a259be5b9c8f572339279734b60ac2afd93ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
|Atributos personalizados|Usado para adicionar atributos para a classe do código gerado.|\<Nenhum >|  
|Gera dois derivado|Se `True`, uma classe base e uma classe parcial (para dar suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, será fornecido um construtor personalizado no código-fonte. Para obter mais informações, consulte [substituir e estender as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificador de herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir do diagrama (`none`, `abstract` ou `sealed`).|Nenhum|  
|Diagrama de base|A classe base do diagrama.|(nenhum)|  
|Nome|O nome do diagrama.|Nome atual|  
|Namespace|O namespace que é associado a este diagrama.|Namespace atual|  
|Classe representada|A classe de domínio raiz que este diagrama representa.|Classe raiz atual se aplicável|  
|Observações|Anotações informais que estão associadas esse elemento.|\<Nenhum >|  
|Cor de preenchimento expõe como propriedade|Se `True`, o usuário pode definir a cor de preenchimento do diagrama do designer gerado. Para configurar isso, clique com botão direito na forma de diagrama e clique em **Explosed adicionar**.|False|  
|Expõe a cor do texto como propriedade|Se `True`, o usuário pode definir a cor do texto do diagrama no designer de gerado. Para configurar isso, clique com botão direito na forma de diagrama e clique em **Explosed adicionar**.|False|  
|Descrição|A descrição é usada para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para este diagrama.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar Ajuda F1 do diagrama.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)