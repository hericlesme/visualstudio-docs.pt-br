---
title: Adicionar novas fontes de dados | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 865f575aefedb5813a72d7a0bb2024bc85313db0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="add-new-data-sources"></a>Adicionar novas fontes de dados
No contexto das ferramentas de dados .NET no Visual Studio, o termo *fonte de dados* refere-se a objetos .NET que se conectar a um repositório de dados e expõem os dados a um aplicativo .NET. Os designers do Visual Studio podem consumir a saída da fonte de dados para gerar o código de boilerplate que vincula os dados para formulários, quando você arrasta e solta os objetos de banco de dados do **fontes de dados** janela. Esse tipo de fonte de dados pode ser:  
  
-   Uma classe em um modelo do Entity Framework que está associado com algum tipo de banco de dados.  
  
-   Um conjunto de dados que está associado com algum tipo de banco de dados.  
  
-   Uma classe que representa um serviço de rede como um serviço de dados do Windows Communication Foundation (WCF) ou um serviço REST.  
  
-   Uma classe que representa um serviço do SharePoint.  
  
-   Uma classe ou uma coleção em sua solução.  
  
> [!NOTE]
>  Se você não estiver usando recursos de associação de dados, conjuntos de dados, o Entity Framework, o LINQ to SQL, WCF ou o SharePoint, o conceito de uma fonte de dados"" não é aplicável. Basta conectar-se diretamente ao banco de dados usando os objetos SQLCommand e se comunicar diretamente com o banco de dados.  
  
 Criar e editar fontes de dados usando o **Assistente de configuração de fonte de dados** em um aplicativo Windows Forms ou Windows Presentation Foundation. Para Entity Framework, primeiro crie suas classes de entidade e, em seguida, inicie o assistente selecionando **projeto** > **adicionar nova fonte de dados** (descritos em mais detalhes posteriormente neste artigo).  
  
 ![Assistente de configuração da fonte de dados](../data-tools/media/data-source-configuration-wizard.png "Assistente de configuração da fonte de dados")  
  
 Depois de criar uma fonte de dados, ele aparece no **fontes de dados** janela da ferramenta (Alt + Shift + D ou **exibição** > **outras janelas**  >  **Fonte de dados**). Você pode arrastar uma fonte de dados de **fontes de dados** janela em uma superfície de design do formulário ou controle. Isso faz com que o código clichê seja gerado, o código que exibe os dados que se origina no repositório de dados para o usuário. A ilustração a seguir mostra um conjunto de dados foi descartado em um Windows form. Se você selecionou F5 no aplicativo, os dados do banco de dados subjacente apareceria em controles do formulário.  
  
 ![Operação de arrastar a fonte de dados](../data-tools/media/raddata-data-source-drag-operation.png "raddata fonte de dados de operação de arrastar")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Fonte de dados para um banco de dados ou um arquivo de banco de dados  
  
### <a name="dataset"></a>Conjunto de dados  
 Para criar um conjunto de dados como uma fonte de dados, execute o **Assistente de configuração de fonte de dados** (**projeto** > **adicionar nova fonte de dados**) e escolha o  **Banco de dados** tipo de fonte de dados. Siga os prompts para especificar uma conexão de banco de dados novo ou existente, ou um arquivo de banco de dados.  
  
### <a name="entity-classes"></a>Classes de entidade  
 Para criar um modelo do Entity Framework como uma fonte de dados, primeiro execute o **Assistente de modelo de dados de entidade** para criar as classes de entidade (**projeto** > **Adicionar Novo Item**  >  **Modelo de dados de entidade ADO.NET**).  
  
 ![Novo item de projeto de modelo do Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata item de projeto de modelo de nova Entity Framework")  
  
 Escolha o método pelo qual você deseja gerar o modelo.  
  
 ![Assistente de modelo de dados de entidade](../data-tools/media/raddata-entity-data-model-wizard.png "raddata Assistente de modelo de dados de entidade")  
  
 Adicione o modelo como uma fonte de dados. As classes que foram geradas aparecem no **Assistente de configuração de fonte de dados** quando você escolhe o **objetos** categoria.  
  
 ![Assistente de configuração de fonte de dados com Classes de entidade](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata Assistente de configuração de fonte de dados com Classes de entidade")  
  
## <a name="data-source-for-a-service"></a>Fonte de dados para um serviço  
 Para criar uma fonte de dados de um serviço, execute o **Assistente de configuração de fonte de dados** e escolha o **Service** tipo de fonte de dados. Isso é apenas um atalho para o **adicionar referência de serviço** caixa de diálogo, você também pode acessar clicando com o projeto no **Solution Explorer** e selecionando **adicionar referência de serviço** .  
  
 Quando você cria uma fonte de dados de um serviço, o Visual Studio adiciona uma referência de serviço ao seu projeto. O Visual Studio também cria os objetos de proxy que correspondem aos objetos que o serviço retorna. Por exemplo, um serviço que retorna um conjunto de dados é representado no seu projeto como um conjunto de dados; um serviço que retorna que um tipo específico é representado no seu projeto como o tipo retornada.  
  
 Você pode criar uma fonte de dados entre os seguintes tipos de serviços:  
  
-   WCF Data Services. Para obter mais informações, consulte [visão geral](/dotnet/framework/data/wcf/wcf-data-services-overview).  
  
-   Serviços WCF. Para obter mais informações, consulte [serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Serviços da Web.  
  
    > [!NOTE]
    >  Os itens que aparecem no **fontes de dados** janela são dependentes dos dados que o serviço retorna. Alguns serviços não podem fornecer informações suficientes para o **Assistente de configuração de fonte de dados** para criar objetos ligáveis. Por exemplo, se o serviço retorna um dataset não tipado, nenhum item aparecerá no **fontes de dados** janela quando você concluir o assistente. Isso ocorre porque datasets tipados não fornecem um esquema e, portanto, o assistente não tem informações suficientes para criar a fonte de dados.  
  
## <a name="data-source-for-an-object"></a>Fonte de dados para um objeto  
 Você pode criar uma fonte de dados de qualquer objeto que expõe uma ou mais propriedades públicas, executando o **Assistente de configuração de fonte de dados** e, em seguida, selecionando o **objeto** tipo de fonte de dados. Todas as propriedades públicas de um objeto são exibidas no **fontes de dados** janela.   Se você estiver usando o Entity Framework e gerou um modelo, isso é onde você pode encontrar as classes de entidade que serão as fontes de dados para seu aplicativo.  
  
 Sobre o **selecionar os objetos de dados** página, expanda os nós na exibição de árvore para localizar os objetos que você deseja associar a. O modo de exibição de árvore contém nós para seu projeto e assemblies e outros projetos que são referenciados pelo seu projeto.  
  
 Se você deseja vincular a um objeto em um assembly ou o projeto que não aparecem na exibição de árvore, clique em **adicionar referência** e usar o **caixa de diálogo Adicionar referência** para adicionar uma referência para o assembly ou o projeto. Depois de adicionar a referência, o assembly ou o projeto é adicionado à exibição em árvore.  
  
> [!NOTE]
>  Talvez seja necessário compilar o projeto que contém os objetos antes dos objetos aparecem na exibição de árvore.  
  
> [!NOTE]
>  Para dar suporte a associação de dados de arrastar e soltar, os objetos que implementam o <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource> interface deve ter um construtor padrão. Caso contrário, o Visual Studio não é possível instanciar o objeto de fonte de dados, e ele exibirá um erro quando você arrastar o item para a superfície de design.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Fonte de dados para uma lista do SharePoint  
 Você pode criar uma fonte de dados de uma lista do SharePoint executando o **Assistente de configuração de fonte de dados** e selecionando o **SharePoint** tipo de fonte de dados. SharePoint expõe dados por meio de [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], portanto, criar uma fonte de dados do SharePoint é o mesmo que criar uma fonte de dados de um serviço. Selecionando o **SharePoint** item o **Assistente de configuração de fonte de dados** abre o **adicionar referência de serviço** caixa de diálogo, em que você se conectar ao serviço de dados do SharePoint ao apontar para o servidor do SharePoint.  Isso requer o SDK do SharePoint.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)