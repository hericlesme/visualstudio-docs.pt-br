---
title: "Visão geral do Visual Studio Object Relational Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: c493a7ea448277275072ab71cf013333ccb9b4ea
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL Tools no Visual Studio
O LINQ to SQL foi a primeira tecnologia de mapeamento relacional de objeto lançada pela Microsoft. Ela funciona bem em cenários básicos e continua a ter suporte no Visual Studio, mas ele não está mais em desenvolvimento ativo. Use o LINQ to SQL durante a manutenção de um aplicativo herdado que já está usando ou em aplicativos simples que usam o SQL Server e não exigem o mapeamento de várias tabela. Em geral, novos aplicativos devem usar o Entity Framework quando uma camada de mapeador relacional de objeto é necessária.  
  
No Visual Studio, você pode criar LINQ para SQL classes que representam as tabelas do SQL usando o Object Relational Designer (O/R Designer).  
  
O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tem duas áreas diferentes em sua superfície de design: o painel de entidades à esquerda e à direita do painel de métodos. O painel das entidades é a principal superfície de design que exibe as classes de entidade, as associações, e hierarquias de herança. O painel de métodos é a superfície de design que exibe o <xref:System.Data.Linq.DataContext> métodos que são mapeados para os procedimentos armazenados e funções.  
  
O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornece uma superfície de design visual para a criação de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classes de entidade e associações (relações) que são baseadas em objetos em um banco de dados. Ou seja, o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é usado para criar um modelo de objeto em um aplicativo que mapeia para objetos em um banco de dados. Ele também gera um <xref:System.Data.Linq.DataContext> fortemente tipado que é usado para enviar e receber dados entre as classes de entidade e o banco de dados. O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] também fornece funcionalidade para mapear os procedimentos armazenados e funções para métodos <xref:System.Data.Linq.DataContext> para retornar dados e preencher classes de entidade. Finalmente, o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornece a capacidade de criar relações de herança entre classes de entidade.  
  
## <a name="opening-the-or-designer"></a>Abrindo object relational Designer de Objetos  
 Para adicionar um LINQ no modelo de entidade SQL ao seu projeto, escolha **projeto**, **Adicionar Novo Item** e, em seguida, escolha **Classes LINQ to SQL** da lista de itens de projeto:  
  
 ![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata Classes LINQ to SQL")  
  
 O Visual Studio cria um arquivo dbml e o adiciona à sua solução. Este é o arquivo de mapeamento de XML e seus arquivos de código relacionadas.  
  
 ![Classes LINQ to SQL no Gerenciador de soluções](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes no Gerenciador de soluções")  
  
 Quando você seleciona o arquivo dbml, o Visual Studio mostra a superfície de Object Relational designer que permite criar visualmente o modelo. A ilustração a seguir mostra o designer após tem sido arrastadas as tabelas Northwind clientes e pedidos do Gerenciador de servidores. Observe a relação entre as tabelas.  
  
 ![O LINQ to SQL Designer](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL de Designer")  
  
> [!IMPORTANT]
>  O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é um mapeador relacional de objeto simples, pois suporta apenas a relações do mapeamento 1:1. Em outras palavras, uma classe de entidade pode ter apenas uma relação de mapeamento de 1:1 com uma tabela ou exibição de banco de dados. Não há suporte para o mapeamento complexas, como uma classe de entidade de mapeamento para uma tabela associada, Use o Entity Framework para mapeamento complexas. Além disso, o designer é um gerador de código unidirecional. Isso significa que somente as alterações feitas à superfície de designer são refletidas no arquivo de código. Alterações manuais ao arquivo de código não são refletidas no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. As alterações que você fizer manualmente no arquivo de código são substituídas quando o designer é salvo e o código for gerado novamente. Para obter informações sobre como adicionar código de usuário e estender as classes geradas pelo [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consulte [como: estender o código gerado por Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Criando e configurando o DataContext  
 Depois de adicionar um **Classes LINQ to SQL** item a um projeto e abra o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], a superfície de design vazio representa vazio <xref:System.Data.Linq.DataContext> pronto para ser configurado. o <xref:System.Data.Linq.DataContext> é configurado com informações de conexão fornecidas pelo primeiro item é arrastado para a superfície de design. Portanto, o <xref:System.Data.Linq.DataContext> é configurada usando as informações de conexão do primeiro item descartado na superfície de design. Para obter mais informações sobre o <xref:System.Data.Linq.DataContext> , consulte classe [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Criando classes de entidade que mapeiam as tabelas de base de dados e modos de exibição  
 Você pode criar classes de entidade mapeados para tabelas e exibições arrastando as tabelas do banco de dados e exibições de **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Conforme indicado na seção anterior a <xref:System.Data.Linq.DataContext> é configurado com informações de conexão fornecidas pelo primeiro item é arrastado para a superfície de design. Se um item subsequente que usa uma conexão diferente é adicionado a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], você pode alterar a conexão para <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [como: criar classes LINQ to SQL mapeadas para tabelas e exibições (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Criando os métodos DataContext que chamam procedimentos armazenados e funções  
 Você pode criar <xref:System.Data.Linq.DataContext> métodos que chamam (são mapeados para) procedimentos armazenados e funções arrastando-os do **Server Explorer**/**Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Os procedimentos armazenados e funções são adicionados a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como métodos de <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Quando você arrasta os procedimentos armazenados e funções de **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], o tipo de retorno de gerado <xref:System.Data.Linq.DataContext> difere do método Dependendo de onde você solta o item. Para obter mais informações, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurando um DataContext para usar procedimentos armazenados para salvar dados entre classes de entidade e um base de dados  
 Conforme observado anteriormente, você pode criar os métodos de <xref:System.Data.Linq.DataContext> que chamam procedimentos armazenados e funções. Além disso, você também pode atribuir procedimentos armazenados que podem ser usados para o comportamento padrão de tempo de execução de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que executa inserções, atualiza, e exclui as. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Herança e object relational Designer de Objetos  
 Como outros objetos, classes de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] podem usar a herança e ser derivadas de outras classes. Em uma base de dados, as relações de herança são criadas de várias maneiras. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais. Para obter mais informações, consulte [como: configurar a herança usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL  
 As classes de entidade criadas pelo [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] são projetados para uso com [LINQ (consulta integrada à linguagem)](/dotnet/csharp/linq/). Para obter mais informações, consulte [como: consulta para obter informações](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separando o DataContext e o código de classe de entidade gerados em diferentes namespaces  
 O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornece o **contexto Namespace** e **entidade Namespace** propriedades no <xref:System.Data.Linq.DataContext>. Essas propriedades que determinam o namespace <xref:System.Data.Linq.DataContext> e o código de classe de entidade são gerados. Por padrão, essas propriedades são vazios e <xref:System.Data.Linq.DataContext> e classes de entidade são gerados no namespace do aplicativo. Para gerar o código em um namespace diferente do namespace do aplicativo, insira um valor para o **contexto Namespace** e/ou **entidade Namespace** propriedades.
  
## <a name="reference-content"></a>Conteúdo de referência
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>Consulte também
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[Perguntas frequentes (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 