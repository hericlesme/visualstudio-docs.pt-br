---
title: "Dados de classe herança (O R Designer) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 13864f690af8b57cc23a218e20a098002e70a2ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="data-class-inheritance-or-designer"></a>Herança de classe de dados (Object Relational Designer)
Como outros objetos, classes de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] podem usar a herança e ser derivadas de outras classes. Em código, você pode especificar relações de herança entre objetos declarando uma classe que herda de outra. Em uma base de dados, as relações de herança são criadas de várias maneiras. [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais.  
  
 A herança de tabela única, há uma única tabela de base de dados que contém colunas para ambos base e classes derivadas. Com dados relacionais, uma coluna de discriminador contém o valor que determina qual classe qualquer determinado registro pertence. Por exemplo, considere pessoas a tabela que contém todos empregado por uma empresa. Algumas pessoas são funcionários e algumas pessoas são gerentes. A tabela de pessoas contém uma coluna denominada o tipo que possui um valor de 1 para gerentes e um valor de 2 para funcionários. A coluna tipo é a coluna de discriminador. Nesse cenário, você pode criar uma subclasse de funcionários e preencher a classe com apenas os registros que têm um valor de tipo de 2.  
  
 Quando você configura herança em classes de entidade usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arraste a tabela única que contém os dados de herança para o designer duas vezes: uma vez para cada classe na hierarquia de herança. Depois de adicionar as tabelas para o designer, conecte-os com um item de herança do **Object Relational Designer** caixa de ferramentas e, em seguida, defina as quatro propriedades de herança no **propriedades** janela.  
  
## <a name="inheritance-properties"></a>Propriedades de herança  
 A seguinte tabela lista as propriedades de herança e suas descrições:  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|Propriedade Discriminatória|A propriedade (mapeado para a coluna) que determina qual classe ao registro atual pertence.|  
|Valor Discriminador de Classe Base|O valor (na coluna desejada como a propriedade de discriminador) que determina que um registro é a classe base.|  
|Valor Discriminatório da Classe Derivada|O valor (na propriedade designada como a propriedade de discriminador) que determina que um registro é derivada da classe.|  
|Padrão de Herança|A classe que deve ser preenchida quando o valor na propriedade designado como o **propriedade discriminatória** não coincide com o o **valor Discriminatório da classe Base** ou **classe derivada Valor Discriminatório**.|  
  
 Criar um modelo de objeto que usar herança e corresponde a dados relacionais pode ser um pouco confuso. Este tópico fornece informações sobre os conceitos básicos e as propriedades individuais que são necessários configurando a herança. Os tópicos a seguir fornecem uma explicação mais claro de como configurar a herança com [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Como: configurar a herança usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Descreve como configurar classes de entidade que usam herança de tabela única usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
|[Passo a passo: Criando Classes LINQ to SQL usando a herança de tabela única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Fornece instruções passo a passo sobre como configurar classes de entidade que usam herança de tabela única usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Passo a passo: Criando Classes LINQ to SQL (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Passo a passo: Criando Classes LINQ to SQL usando a herança de tabela única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Introdução](/dotnet/framework/data/adonet/sql/linq/getting-started)