---
title: 'Passo a passo: Criando uma lista externa no SharePoint usando dados corporativos | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c0954665e8b088f969d59bdad0a2ef1207c95c8f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>Instruções passo a passo: criando uma lista externa no SharePoint usando dados corporativos
  O serviço de conectividade de dados de negócios (BDC) permite que o SharePoint exibir dados de negócios de aplicativos de servidor back-end, serviços Web e bancos de dados.  
  
 Este passo a passo mostra como criar um modelo para o serviço de catálogo de dados corporativos que retorna informações sobre contatos em um banco de dados de exemplo. Você, em seguida, criará uma lista externa no SharePoint usando este modelo.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto.  
  
-   Adicionando uma entidade no modelo.  
  
-   Adicionando um método finder.  
  
-   Adicionando um método finder específico.  
  
-   O projeto de teste.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)], ou [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Acesso ao banco de dados de exemplo AdventureWorks. Para obter mais informações sobre como instalar o banco de dados AdventureWorks, consulte [bancos de dados de exemplo do SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483).  
  
## <a name="creating-a-project-that-contains-a-bdc-model"></a>Criando um Projeto que Contenha um Modelo de BDC  
  
#### <a name="to-create-a-project-that-contains-a-bdc-model"></a>Para criar um projeto que contenha um modelo BDC  
  
1.  Na barra de menus do Visual Studio, escolha **arquivo**, **novo**, **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
2.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** item.  
  
3.  No **modelos** painel, escolha **projeto do SharePoint 2010**, nomeie o projeto **AdventureWorksTest**e, em seguida, escolha o **Okey** botão .  
  
     O **Assistente de personalização do SharePoint** é exibida. Neste assistente, você pode especificar o site que você usará para depurar o projeto e defina o nível de confiança da solução.  
  
4.  Escolha o **implantar como uma solução de farm** botão de opção para definir o nível de confiança.  
  
5.  Escolha o **concluir** botão para aceitar o site padrão local do SharePoint.  
  
6.  Em **Solution Explorer**, escolha o nó do projeto do SharePoint.  
  
7.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
8.  No **modelos** painel, escolha **modelo de conectividade de dados corporativos (solução de Farm somente)**, nomeie o projeto **AdventureWorksContacts**e, em seguida, escolha o **Adicionar** botão.  
  
## <a name="adding-data-access-classes-to-the-project"></a>Adicionando Classes de Acesso a Dados ao Projeto  
  
#### <a name="to-add-data-access-classes-to-the-project"></a>Para adicionar classes de acesso a dados ao projeto  
  
1.  Na barra de menus, escolha **ferramentas**, **conectar-se ao banco de dados**.  
  
     O **Adicionar Conexão** caixa de diálogo é aberta.  
  
2.  Adicione uma conexão ao banco de dados de exemplo AdventureWorks do SQL Server.  
  
     Para obter mais informações, consulte [Adicionar/Modificar Conexão (Microsoft SQL Server)](http://msdn.microsoft.com/en-us/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  Em **Solution Explorer**, escolha o nó do projeto.  
  
4.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
5.  No **modelos instalados** painel, escolha o **dados** nó.  
  
6.  No **modelos** painel, escolha **Classes LINQ to SQL**.  
  
7.  No **nome** , especifique **AdventureWorks**e, em seguida, escolha o **adicionar** botão.  
  
     Um arquivo dbml é adicionado ao projeto e abre o Object Relational Designer (O/R Designer).  
  
8.  Na barra de menus, escolha **exibição**, **Server Explorer**.  
  
9. Em **Server Explorer**, expanda o nó que representa o banco de dados de exemplo AdventureWorks e, em seguida, expanda o **tabelas** nó.  
  
10. Adicionar o **contato (pessoa)** tabela para o O/R Designer.  
  
     Uma classe de entidade é criada e aparece na superfície de design. A classe da entidade tem propriedades que são mapeados para as colunas na tabela Contact (pessoa).  
  
## <a name="removing-the-default-entity-from-the-bdc-model"></a>Removendo a Entidade Padrão do Modelo BDC  
 O **modelo de conectividade de dados corporativos** projeto adiciona uma entidade padrão chamada Entity1 para o modelo. Remova esta entidade. Posteriormente, você adicionará uma nova entidade. Começando com um modelo vazio reduz o número de etapas necessárias para concluir o passo a passo.  
  
#### <a name="to-remove-the-default-entity-from-the-model"></a>Para remover a entidade padrão do modelo  
  
1.  Em **Solution Explorer**, expanda o **BdcModel1** nó e, em seguida, abra o arquivo BdcModel1.bdcm.  
  
2.  O arquivo de modelo de conectividade de dados corporativos é aberto no designer de BDC.  
  
3.  No designer, abra o menu de atalho para **Entity1**e, em seguida, escolha **excluir**.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para Entity1.vb (no Visual Basic) ou Entity1.cs (em c#) e, em seguida, escolha **excluir**.  
  
5.  Abra o menu de atalho para Entity1Service.vb (no Visual Basic) ou Entity1Service.cs (em c#) e, em seguida, escolha **excluir**.  
  
## <a name="adding-an-entity-to-the-model"></a>Adicionando uma Entidade ao Modelo  
 Adicione uma entidade no modelo. Você pode adicionar entidades do Visual Studio **caixa de ferramentas** para o designer BDC.  
  
#### <a name="to-add-an-entity-to-the-model"></a>Para adicionar uma Entidade ao modelo  
  
1.  Na barra de menus, escolha **Exibir**, **Caixa de Ferramentas**.  
  
2.  No **BusinessDataConnectivity** guia do **caixa de ferramentas**, adicionar um **entidade** para o designer BDC.  
  
     A nova entidade é exibida no designer. O Visual Studio adiciona um arquivo que é nomeado EntityService.vb (no Visual Basic) ou EntityService.cs (em c#) para o projeto.  
  
3.  Na barra de menus, escolha **exibição**, **propriedades**, **janela**.  
  
4.  No **propriedades** janela, defina o **nome** valor da propriedade **entre em contato com**.  
  
5.  No designer, abra o menu de atalho para a entidade, escolha **adicionar**e, em seguida, escolha **identificador**.  
  
     Um novo identificador aparece na entidade.  
  
6.  No **propriedades** janela, altere o nome do identificador para **ContactID**.  
  
7.  No **nome do tipo** , escolha **System. Int32**.  
  
## <a name="adding-a-specific-finder-method"></a>Adicionando um Método de Localizador Específico  
 Para habilitar o serviço BDC exibir um contato específico, você deve adicionar um método Finder específico. O serviço BDC chama o método Finder específico quando um usuário escolhe um item em uma lista e, em seguida, escolhe a **Item de exibição** botão na faixa de opções.  
  
 Adicionar um método Finder específico para a entidade Contact usando o **detalhes de método BDC** janela. Para retornar uma entidade específica, adicione código ao método.  
  
#### <a name="to-add-a-specific-finder-method"></a>Para adicionar um método de Localizador Específico  
  
1.  No designer de BDC, escolha o **contato** entidade.  
  
2.  Na barra de menus, escolha **exibição**, **outras janelas**, **detalhes de método BDC**.  
  
     Abre a janela de detalhes de método BDC.  
  
3.  No **adicionar um método** , escolha **criar o método Finder específico**.  
  
     O Visual Studio adiciona os seguintes elementos ao modelo. Esses elementos aparecem no **detalhes de método BDC** janela.  
  
    -   Um método chamado ReadItem.  
  
    -   Um parâmetro de entrada para o método.  
  
    -   Um parâmetro de retorno do método.  
  
    -   Um descritor de tipo para cada parâmetro.  
  
    -   Uma instância de método para o método.  
  
4.  No **detalhes de método BDC** janela, abra a lista que aparece para o **contato** descritor de tipo e, em seguida, escolha **editar**.  
  
     O **Explorer BDC** é aberta e oferece uma exibição hierárquica do modelo.  
  
5.  No **propriedades** janela, abra a lista ao lado a **TypeName** propriedade, escolha o **projeto atual** guia e, em seguida, escolha o **contato**propriedade.  
  
6.  No **BDC Explorer**, abra o menu de atalho a **entre em contato com**e, em seguida, escolha **Adicionar descritor de tipo**.  
  
     Um novo descritor de tipo denominado **TypeDescriptor1** aparece no **Explorer BDC**.  
  
7.  No **propriedades** janela, defina o **nome** valor da propriedade **ContactID**.  
  
8.  Abra a lista ao lado de **TypeName** propriedade e, em seguida, escolha **Int32**.  
  
9. Abra a lista ao lado de **identificador** propriedade e, em seguida, escolha **ContactID**.  
  
10. Repita a etapa 6 para criar um descritor de tipo para cada um dos campos a seguir.  
  
    |Nome|Nome do tipo|  
    |----------|---------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Telefone|System.String|  
    |endereço de email|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. No designer de BDC, sobre o **entre em contato com** entidade, abra o **ReadItem** método.  
  
     O arquivo de código de serviço de contato é aberto no Editor de código.  
  
12. No `ContactService` classe, substitua o `ReadItem` método com o código a seguir. Esse código executa as seguintes tarefas:  
  
    -   Recupera um registro da tabela de contatos do banco de dados AdventureWorks.  
  
    -   Retorna uma entidade de contato para o serviço de catálogo de dados corporativos.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="adding-a-finder-method"></a>Adicionando um Método de Localizador  
 Para habilitar o serviço BDC exibir os contatos em uma lista, você deve adicionar um método Finder. Adicionar um método Finder para a entidade Contact usando o **detalhes de método BDC** janela. Para retornar uma coleção de entidades para o serviço de catálogo de dados corporativos, adicione código ao método.  
  
#### <a name="to-add-a-finder-method"></a>Para adicionar um método de Localizador  
  
1.  No designer de BDC, escolha o **contato** entidade.  
  
2.  No **detalhes de método BDC** janela, recolher o **ReadItem** nó.  
  
3.  No **adicionar um método** lista sob o **ReadList** método, escolha **criar método do localizador**.  
  
     O Visual Studio adiciona um método, um parâmetro de retorno e um descritor de tipo.  
  
4.  No designer de BDC, sobre o **entre em contato com** entidade, abra o **ReadList** método.  
  
     O arquivo de código para o serviço de contato é aberto no Editor de código.  
  
5.  No `ContactService` classe, substitua o `ReadList` método com o código a seguir. Esse código executa as seguintes tarefas:  
  
    -   Recupera dados da tabela de contatos do banco de dados AdventureWorks.  
  
    -   Retorna uma lista de entidades de contato para o serviço de catálogo de dados corporativos.  
  
    > [!NOTE]  
    >  Substitua o valor da `ServerName` campo com o nome do servidor.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="testing-the-project"></a>O projeto de teste  
 Quando você executar o projeto, abre o site do SharePoint e o Visual Studio adiciona o modelo para o serviço de conectividade de dados corporativos. Crie uma lista externa no SharePoint que faz referência à entidade de contato. Os dados de contatos no banco de dados AdventureWorks aparecem na lista.  
  
> [!NOTE]  
>  Você talvez precise modificar configurações de segurança do SharePoint para poder depurar sua solução.  Para obter mais informações, consulte [criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### <a name="to-test-the-project"></a>Para testar o projeto  
  
1.  Pressione a tecla **F5**.  
  
     Abre o site do SharePoint.  
  
2.  Sobre o **ações do Site** menu, escolha o **mais opções** comando.  
  
3.  No **criar** página, escolha o **lista externa** modelo e, em seguida, escolha o **criar** botão.  
  
4.  Nome de lista personalizada **contatos**.  
  
5.  Escolha o botão Procurar ao lado de **tipo de conteúdo externo** campo.  
  
6.  No **seletor de tipo de conteúdo externo** caixa de diálogo caixa, escolha o **AdventureWorksContacts.BdcModel1.Contact** item e, em seguida, escolha o **criar** botão.  
  
     O SharePoint cria uma lista externa que contenha contatos do banco de dados de exemplo AdventureWorks.  
  
7.  Para testar o método Finder específico, escolha um contato na lista.  
  
8.  Na faixa de opções, escolha o **itens** guia e, em seguida, escolha o **Item de exibição** comando.  
  
     Os detalhes do contato que você escolheu aparecem em um formulário.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como criar modelos para o serviço de catálogo de dados corporativos no SharePoint com estes tópicos:  
  
-   [Como: adicionar um método Creator](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Como: adicionar um método Updater](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Como: adicionar um método Deleter](../sharepoint/how-to-add-a-deleter-method.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Criando um modelo de conectividade de dados corporativos](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Visão geral de ferramentas de Design de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Integrando dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  