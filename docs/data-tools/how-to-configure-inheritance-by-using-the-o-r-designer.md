---
title: "Como: configurar a herança usando o Designer O-R | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b53dec270481ca8aa6009b9ddd27bdcdfeae6037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Como: configurar a herança usando Object Relational Designer
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais. Na tabela única de herança, há uma tabela de banco de dados único que contém campos para as informações de pai e informações de filho. Com dados relacionais, uma coluna discriminatória contém o valor que determina qual classe qualquer registro pertence.  
  
Por exemplo, considere pessoas a tabela que contém todos empregado por uma empresa. Algumas pessoas são funcionários e algumas pessoas são gerentes. A tabela de pessoas contém uma coluna chamada `EmployeeType` que tenha um valor de 1 para gerentes e um valor de 2 para funcionários; esta é a coluna de discriminador. Nesse cenário, você pode criar uma subclasse de funcionários e preencher a classe com apenas os registros que têm um valor de `EmployeeType` de 2. Você pode também remover colunas que não se aplicam de cada uma das classes.  
  
Criar um modelo de objeto que usar herança (e corresponde a dados relacionais) pode ser um pouco confuso. O procedimento a seguir descreve as etapas necessárias para configurar a herança com object relational Designer de Objetos. Após as etapas genéricos sem se referir a uma tabela existente e colunas pode ser difícil, para uma explicação passo a passo que usa dados é fornecido. Para instruções passo a passo detalhadas para configurar a herança usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consulte [passo a passo: Criando Classes LINQ to SQL, usando a herança de tabela única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
## <a name="to-create-inherited-data-classes"></a>Para criar classes de dados herdadas
  
1.  Abra o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] adicionando um **Classes LINQ to SQL** item a um projeto existente do Visual Basic ou c#.  
  
2.  Arraste a tabela que você deseja usar como a classe base em [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Arraste uma segunda cópia da tabela para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e renomeá-lo. Esta é a classe derivada, ou subclasse.  
  
4.  Clique em **herança** no **Object Relational Designer** guia do **caixa de ferramentas**e, em seguida, clique a subclasse (a tabela que você renomeou) e conectá-lo para a classe base.  
  
    > [!NOTE]
    >  Clique o **herança** item o **caixa de ferramentas** e solte o botão do mouse, clique a segunda cópia da classe que você criou na etapa 3 e, em seguida, clique na primeira classe que você criou na etapa 2. A seta na linha de herança irá apontar para a primeira classe.  
  
5.  Em cada classe, excluir todas as propriedades do objeto que você não deseja que apareça e que não são usadas para associações. Você receberá um erro se você tentar excluir propriedades de objeto usadas para associações: [a propriedade \<nome da propriedade > não pode ser excluída porque participa da associação \<nome da associação >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Como uma classe derivada herda as propriedades definidas na sua classe base, as mesmas colunas não podem ser definidas em cada classe. (As colunas são implementadas como propriedades.) Você pode ativar a criação das colunas na classe derivada definindo o modificador de herança na propriedade na classe base. Para obter mais informações, consulte [Noções básicas de herança (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).  
  
6.  Selecione a linha de herança em [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
7.  No **propriedades** janela, defina o **propriedade discriminatória** para o nome da coluna que é usado para distinguir os registros de suas classes.  
  
8.  Definir o **valor Discriminatório da classe derivada** propriedade para o valor no banco de dados que designa o registro como o tipo herdado. (Esse é o valor que são armazenados na coluna de discriminador e que é usado para designar a classe herdada.)  
  
9. Definir o **valor Discriminatório da classe Base** propriedade para o valor que designa o registro como um tipo base. (Esse é o valor que são armazenados na coluna de discriminador e que é usado para designar a classe base.)  
  
10. Opcionalmente, você também pode definir o **padrão de herança** propriedade para designar um tipo em uma hierarquia de herança usado ao carregar linhas que não corresponde a nenhum código de herança definido. Em outras palavras, se um registro tem um valor em uma coluna discriminatória que não coincide com o valor no **valor Discriminatório da classe derivada** ou **valor Discriminatório da classe Base** propriedades, o registro será carregado para o tipo designado como o **padrão de herança**.  
  
## <a name="see-also"></a>Consulte também
[LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Passo a passo: Criando Classes LINQ to SQL (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[Accessing data in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  (Acessando dados no Visual Studio)  
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Passo a passo: Criando Classes LINQ to SQL usando a herança de tabela única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
[Noções básicas de herança (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)  
[Herança](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)