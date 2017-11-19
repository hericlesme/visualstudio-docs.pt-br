---
title: 'Passo a passo: Criando uma Web Part do Silverlight que exiba OData para o SharePoint | Microsoft Docs'
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a6999a7a390c207c184f26d36e0ca5d64d5fef5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Passo a passo: Criando um web part do Silverlight que exiba OData para o SharePoint
  SharePoint 2010 expõe seus dados de lista por meio do OData. No SharePoint, o serviço OData é implementado pelo serviço RESTful ListData.svc. Este passo a passo mostra como criar uma web part do SharePoint que hospeda um aplicativo do Silverlight. O aplicativo do Silverlight exibe informações de lista de lançamento do SharePoint usando ListData.svc. Para obter mais informações, consulte [Interface REST do SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) e [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Microsoft Windows e do SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Criando um aplicativo do Silverlight e uma Web Part do Silverlight  
 Primeiro, crie um aplicativo do Silverlight no Visual Studio. O aplicativo do Silverlight recupera dados da lista de anúncios do SharePoint por meio do serviço ListData.svc.  
  
> [!NOTE]  
>  Nenhuma versão do Silverlight 4.0 antes de suporte as interfaces necessárias para fazer referência a dados de lista do SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Para criar um aplicativo do Silverlight e uma web part do Silverlight  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **projeto** para exibir o **novo projeto** caixa de diálogo.  
  
2.  Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
3.  No painel modelos, escolha o **Web Part do SharePoint 2010 do Silverlight** modelo.  
  
4.  No **nome** , digite **SLWebPartTest** e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** caixa de diálogo é exibida.  
  
5.  Sobre o **especificar o nível de site e segurança de depuração** página, insira a URL do servidor do site do SharePoint onde você deseja depurar a definição de site ou use o local padrão (http://*nome de sistema*/) .  
  
6.  No **o que é o nível de confiança para essa solução do SharePoint?** , escolha o **implantar como uma solução de farm** botão de opção.  
  
     Embora este exemplo usa uma solução de farm, os projetos do Silverlight web part podem ser implantados como farm ou soluções em modo seguro. Para obter mais informações sobre as soluções em modo seguro e soluções de farm, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  No **como você deseja associar a Web Part do Silverlight** seção o **especificar informações de configuração do Silverlight** página, escolha o **criar um novo projeto do Silverlight e associá-lo com a web part** botão de opção.  
  
8.  Alterar o **nome** para **SLApplication**, defina **idioma** como **Visual Basic** ou **Visual C#**, e, em seguida, defina **versão Silverlight** para **Silverlight 4.0**.  
  
9. Escolha o **concluir** botão. Os projetos são exibidos na **Gerenciador de soluções**.  
  
     A solução contém dois projetos: um aplicativo do Silverlight e uma web part do Silverlight. O aplicativo do Silverlight recupera e exibe os dados de lista do SharePoint, e a web part do Silverlight hospeda o aplicativo do Silverlight, permitindo que você exibi-lo no SharePoint.  
  
##  <a name="customizing-the-silverlight-application"></a>Personalizando o aplicativo do Silverlight  
 Adicione elementos de código e de design para o aplicativo do Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Para personalizar o aplicativo do Silverlight  
  
1.  Adicione uma referência de assembly para System.Windows.Data no aplicativo Silverlight. Para obter mais informações, consulte [como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência de serviço**.  
  
    > [!NOTE]  
    >  Se você estiver usando o Visual Basic, você deve escolher o **Mostrar todos os arquivos** no canto superior do **Solution Explorer** para exibir o **referências** nó.  
  
3.  Na caixa de endereço a **adicionar referência de serviço** caixa de diálogo, digite a URL do site do SharePoint, como **http://MySPSite**e, em seguida, escolha o **vá** botão.  
  
     Quando o Silverlight localiza o serviço do SharePoint OData ListData.svc, ele substitui o endereço com a URL do serviço completo. Neste exemplo, http://myserver torna-se http://myserver/_vti_bin/ListData.svc.  
  
4.  Escolha o **Okey** botão para adicionar a referência de serviço para o projeto e, em seguida, use o nome de serviço padrão, ServiceReference1.  
  
5.  Na barra de menus, escolha **Compilar**, **Compilar Solução**.  
  
6.  Adicione uma nova fonte de dados para o projeto com base no serviço do SharePoint. Para fazer isso, na barra de menus, escolha **exibição**, **outras janelas**, **fontes de dados**.  
  
     O **fontes de dados** janela mostra todos os dados de lista do SharePoint disponíveis, como calendário, tarefas e anúncios.  
  
7.  Adicione os dados da lista de avisos para o aplicativo do Silverlight. Você pode arrastar "Anúncios" o **fontes de dados** janela para o Silverlight designer.  
  
     Isso cria um controle de grade associado à lista de anúncios do site do SharePoint.  
  
8.  Redimensione o controle de grade para caber na página do Silverlight.  
  
9. No arquivo de código de MainPage. XAML (MainPage.xaml.cs para Visual c#) ou MainPage do Visual Basic, adicione as seguintes referências de namespace.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Adicione as seguintes declarações de variável na parte superior da classe.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. Substitua o `UserControl_Loaded` procedimento com o seguinte.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     Certifique-se de substituir o *ServerName* espaço reservado com o nome do servidor que está executando o SharePoint.  
  
12. Adicione o seguinte procedimento de tratamento de erros.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modifying-the-silverlight-web-part"></a>Modificando a Web Part do Silverlight  
 Altere uma propriedade usando o projeto de web part do Silverlight para habilitar a depuração do Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Para modificar a web part do Silverlight  
  
1.  Abra o menu de atalho para o projeto de web part do Silverlight (**SLWebPartTest**) e, em seguida, escolha **propriedades**.  
  
2.  No **propriedades** janela, escolha o **SharePoint** guia.  
  
3.  Se ele ainda não estiver selecionado, selecione o **Silverlight Habilitar depuração (em vez de depuração de Script)** caixa de seleção.  
  
4.  Salvar o projeto.  
  
##  <a name="testing-the-silverlight-web-part"></a>Testando a Web Part do Silverlight  
 Teste a nova web part do Silverlight no SharePoint para garantir que ele exibe corretamente os dados de lista do SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Para testar a web part do Silverlight  
  
1.  Pressione a tecla F5 para compilar e executar a solução do SharePoint.  
  
2.  No SharePoint, no **ações do Site** menu, escolha **nova página**.  
  
3.  No **nova página** caixa de diálogo, digite um título, como **SL Web Part teste**e, em seguida, escolha o **criar** botão.  
  
4.  No designer de página, no **ferramentas de edição** guia, escolha **inserir**.  
  
5.  Na faixa de guias, escolha **Web Part**.  
  
6.  No **categorias** caixa, escolha o **personalizado** pasta.  
  
7.  No **Web Parts** lista, escolha a web part do Silverlight e, em seguida, escolha o **adicionar** botão para adicionar a web part para o designer.  
  
8.  Depois de ter feito todas as adições à página da web que você quer, escolha o **página** guia e, em seguida, escolha o **Salvar & Fechar** botão na barra de ferramentas.  
  
     A web part do Silverlight agora deve exibir dados de anúncio do site do SharePoint. Por padrão, a página é armazenada na lista de páginas do Site do SharePoint.  
  
    > [!NOTE]  
    >  Ao acessar dados no Silverlight entre domínios, Silverlight protege contra vulnerabilidades de segurança que podem ser usadas para explorar os aplicativos da web. Se você encontrar problemas ao acessar dados remotos no Silverlight, consulte [tornando um serviço disponível através dos limites do domínio](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Consulte também  
 [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Implantando, publicando e atualizando pacotes de soluções do SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
