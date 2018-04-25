---
title: 'Passo a passo: Criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a6fc193ba73c040042e7d19d5b86f0acf61e69ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Instruções passo a passo: criar uma coluna de site, tipo de conteúdo e lista do SharePoint
  Os procedimentos a seguir demonstram como criar colunas personalizadas de site do SharePoint — ou *campos*— bem como um tipo de conteúdo que usa as colunas de site. Ele também mostra como criar uma lista que usa o novo tipo de conteúdo.  
  
 Esta explicação passo a passo inclui as seguintes tarefas:  
  
-   [Criar um Site personalizado colunas](#BKMK_CreatingCustSiteCols).  
  
-   [Criando um tipo de conteúdo personalizado](#BKMK_CreateCustContType).  
  
-   [Criando uma lista](#BKMK_CreateList).  
  
-   [Criando uma lista](#BKMK_CreateList).  
  
-   [Testando o aplicativo](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Criar colunas de Site personalizadas  
 Este exemplo cria uma lista de gerenciamento de pacientes em um hospital. Primeiro, você deve criar um projeto do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e adicionar colunas de site, da seguinte maneira.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Sobre o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **arquivo** menu, escolha **novo**, **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha **2010**.  
  
3.  No **modelos** painel, escolha **projeto do SharePoint 2010**, altere o nome do projeto para **clínica**e, em seguida, escolha o **Okey** botão.  
  
     O modelo de projeto do SharePoint 2010 é um projeto vazio é usado neste exemplo para conter as colunas de site e outros itens de projeto que forem adicionadas posteriormente.  
  
4.  Sobre o **especificar o nível de site e segurança de depuração** página, insira a URL para o site do SharePoint local para o qual você deseja adicionar o novo item de campo personalizado ou usar o local padrão (`http://<`*SystemName* `>/)`.  
  
5.  No **o que é o nível de confiança para essa solução do SharePoint?** seção, use o valor padrão **implantar como uma solução em área restrita**.  
  
     Para obter mais informações sobre a área restrita e soluções em farm, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Escolha o **concluir** botão. O projeto agora deve ser listado na **Gerenciador de soluções**.  
  
#### <a name="to-add-site-columns"></a>Para adicionar colunas de site  
  
1.  Adicione uma nova coluna de site. Para fazer isso, em **Solution Explorer**, abra o menu de atalho para **clínica**e, em seguida, escolha **adicionar**, **Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha **coluna Site**, altere o nome para **paciente nome**e, em seguida, escolha o **adicionar** botão.  
  
3.  No arquivo de Elements da coluna de site, deixe o **tipo** definindo como **texto**e altere o **grupo** definindo como **clínica Site colunas**. Ao concluir, o arquivo Elements XML da coluna de site deve parecer com o exemplo a seguir.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Usando o mesmo procedimento, adicione mais duas colunas de site para o projeto: **ID do paciente** (tipo = "Integer") e **nome Doctor** (tipo = "Text"). Definir seu valor de grupo **clínica Site colunas**.  
  
##  <a name="BKMK_CreateCustContType"></a> Criando um tipo de conteúdo personalizado  
 Em seguida, crie um tipo de conteúdo, com base no tipo de conteúdo contatos — que inclui as colunas de site que você criou no procedimento anterior. Baseando um tipo de conteúdo em um tipo de conteúdo existente, você pode poupar tempo porque o tipo de conteúdo base fornece várias colunas de site para uso no novo tipo de conteúdo.  
  
#### <a name="to-create-a-custom-content-type"></a>Para criar um tipo de conteúdo personalizado  
  
1.  Adicione um tipo de conteúdo para o projeto. Para fazer isso, em **Solution Explorer**, escolha o nó do projeto  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
3.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  No **modelos** painel, escolha o **tipo de conteúdo** modelo, altere o nome para **paciente informações**e, em seguida, escolha o **adicionar** botão.  
  
     O **Assistente de personalização do SharePoint** é aberto.  
  
5.  No **qual tipo de conteúdo base deste tipo de conteúdo deve herdar de** , escolha **contato** como o tipo de conteúdo no qual basear o novo tipo de conteúdo e, em seguida, escolha o **concluir**botão.  
  
     Isso fornece acesso a outras colunas de site potencialmente útil do tipo de conteúdo de contato, além das colunas de site que você definiu anteriormente.  
  
6.  Após o tipo de conteúdo designer for exibida, no **colunas** guia, adicione os três colunas que você definiu anteriormente do site: **paciente nome**, **ID do paciente**e **Doctor nome**. Para adicionar essas colunas, escolha a primeira caixa de listagem na lista de colunas de site em **nome de exibição**e clique em cada coluna de site na lista um por vez.  
  
    > [!TIP]  
    >  Para escolher as colunas de site mais rapidamente, filtre a lista, digitando as primeiras letras do nome da coluna.  
  
7.  Além das três colunas de um site personalizado, adicione o **comentários** coluna da lista de colunas de site do site.  
  
8.  Selecione o **necessária** caixa de seleção para o **paciente nome** e **ID do paciente** campos obrigatórios de colunas de site para torná-los.  
  
9. No **o tipo de conteúdo** guia, certifique-se de que o nome do tipo de conteúdo é **paciente informações**e, em seguida, altere a descrição para **cartão de informações de pacientes**.  
  
10. Alterar **nome do grupo** para **tipos de conteúdo de clínica**e deixar as outras configurações em seus valores padrão.  
  
11. Na barra de menus, escolha **arquivo**, **Salvar tudo**e, em seguida, feche o designer de tipo de conteúdo.  
  
##  <a name="BKMK_CreateList"></a> Criando uma lista  
 Agora, crie uma lista que usa as novas colunas de site e o tipo de conteúdo.  
  
#### <a name="to-create-a-list"></a>Para criar uma lista  
  
1.  Adicione uma lista ao projeto. Para fazer isso, em **Solution Explorer**, escolha o nó do projeto.  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
3.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  No **modelos** painel, escolha o **lista** modelo, altere o nome para **pacientes**e, em seguida, escolha o **adicionar** botão.  
  
5.  Deixe o **personalizar a lista com base em** definindo como **padrão (em branco)** e, em seguida, escolha o **concluir** botão.  
  
6.  No Designer de lista, escolha o **tipos de conteúdo** botão para exibir o **configurações de tipo de conteúdo** caixa de diálogo.  
  
7.  Escolha a nova linha, escolha o **paciente informações** tipo na lista de tipos de conteúdo de conteúdo e, em seguida, escolha o **Okey** botão.  
  
     Isso adiciona todas as colunas de site do **paciente informações** tipo na lista de conteúdo.  
  
8.  Exclua todas as colunas de site na lista, exceto os seguintes:  
  
    -   ID do paciente  
  
    -   Nome do paciente  
  
    -   Telefone residencial  
  
    -   Email  
  
    -   Nome de DR.  
  
    -   Comentários  
  
9. Em **nome da coluna de exibição**, escolha uma linha vazia, adicionar uma coluna de lista personalizada e nomeie-o **Hospital**. Deixe seu tipo de dados como **linha única de texto**.  
  
     A coluna de lista personalizada se aplica somente a esta lista. Quando você adiciona uma coluna de lista personalizada para uma lista, um nova lista Tipo de conteúdo, incluindo todas as colunas adicionadas à lista, é criado e definido como a lista padrão.  
  
    > [!TIP]  
    >  Se você escolher uma coluna na lista de colunas de site, uma coluna de site existente será usada. No entanto, se você inserir um valor de nome de coluna sem escolher todas as colunas na lista, uma coluna de lista personalizada é criada, mesmo se uma coluna com o mesmo nome já existe na lista.  
  
     Opcionalmente, em vez de definir o tipo de dados da coluna de lista personalizada para **linha única de texto**, em vez disso, você pode definir o tipo de dados para essa coluna para pesquisa e seus valores deve ser recuperados de uma tabela ou outra lista. Para obter informações sobre colunas de pesquisa, consulte [relações de lista do SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) e [pesquisas e as relações de lista](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Ao lado de **ID do paciente** e **paciente nome** caixas, selecionadas o **necessário** caixa de seleção.  
  
11. Sobre o **exibições** guia, selecione uma linha vazia para criar um modo de exibição. Digite **detalhes pacientes**.  
  
     Sobre o **exibições** guia, você pode especificar as colunas que você deseja que apareça na lista do SharePoint.  
  
12. Escolha o novo **paciente detalhes** de linha e, em seguida, escolha o **definido como padrão** botão.  
  
     O novo modo de exibição agora é o modo de exibição padrão da lista.  
  
13. Adicione as seguintes colunas para o **colunas selecionadas** lista na seguinte ordem:  
  
    -   ID do paciente  
  
    -   Nome do paciente  
  
    -   Telefone residencial  
  
    -   Email  
  
    -   Nome de DR.  
  
    -   Hospital  
  
    -   Comentários  
  
14. No **propriedades** , escolha o **classificando e agrupando** propriedade e, em seguida, escolha o botão de reticências ![ícone de reticências](../sharepoint/media/ellipsisicon.gif "ícone de reticências")para exibir o **classificando e agrupando** caixa de diálogo.  
  
15. No **nome de coluna** , escolha **paciente nome**, verifique se o **classificação** coluna é definida como **crescente**e, em seguida, escolha o  **Okey** botão.  
  
##  <a name="BKMK_TestApp"></a> Testando o aplicativo  
 Agora que as colunas de um site personalizado, o tipo de conteúdo e a lista estiverem prontos, implantá-los para o SharePoint e execute o aplicativo para testá-lo.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Na barra de menus, escolha **Arquivo**, **Salvar Todos**.  
  
2.  Escolha a tecla F5 para executar o aplicativo.  
  
     O aplicativo é compilado e, em seguida, seus recursos são implantados no SharePoint e ativados.  
  
3.  Na barra de navegação rápida, escolha o **pacientes** link para exibir o **pacientes** lista.  
  
     Os nomes de coluna na lista devem corresponder com aquelas que você inseriu no **exibições** guia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Escolha o **adicionar novo item** link para criar um cartão de informações de pacientes.  
  
5.  Insira informações para os campos e, em seguida, escolha o **salvar** botão.  
  
     O novo registro aparece na lista.  
  
## <a name="see-also"></a>Consulte também  
 [Criar colunas de Site, tipos de conteúdo e listas do SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Como: criar um tipo de campo personalizado](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Tipos de conteúdo](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Colunas](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  