---
title: "Passo a passo: Criar um projeto de definição de Site básico | Microsoft Docs"
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a792ab750decf1a14b589116d886c847b3ddd478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Passo a passo: Criar um projeto de definição de site básico
  Este passo a passo mostra como criar uma definição de site básico que contém uma Web part visual com alguns controles nele. Para clareza, a Web part visual que você cria tem apenas alguns controles. No entanto, você pode criar mais sofisticadas definições de site do SharePoint que incluem funcionalidade mais.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando uma definição de site usando o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modelo de projeto.  
  
-   Criar um site do SharePoint usando uma definição de site do SharePoint.  
  
-   Adicionar uma Web part visual para a solução.  
  
-   Personalizando a página do site default.aspx adicionando nova Web part visual a ela.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Microsoft Windows e do SharePoint. Para obter mais informações, consulte requisitos para desenvolver soluções do SharePoint.  
  
-   Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Criando uma Solução de Definição do Site  
 Primeiro, crie o projeto de definição de site no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Para criar um projeto de definição do site  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**. Se seu IDE está definido para usar configurações de desenvolvimento do Visual Basic, na barra de menus, escolha **arquivo**, **novo projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Expanda o **Visual C#** nó ou o **Visual Basic** nó, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
3.  No **modelos** , escolha o **projeto do SharePoint 2010** modelo.  
  
4.  No **nome** , digite **TestSiteDef**e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
5.  Sobre o **especificar o nível de site e segurança de depuração** página, insira a URL para o site do SharePoint onde você deseja depurar a definição de site ou use o local padrão (http://*nome do sistema*/).  
  
6.  No **o que é o nível de confiança para essa solução do SharePoint?** , escolha o **implantar como uma solução de farm** botão de opção.  
  
     Todos os projetos de definição de site devem ser implantados como soluções de farm. Para obter mais informações sobre soluções de área restrita em comparação com soluções de farm, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Escolha o **concluir** botão.  
  
     O projeto aparece na **Gerenciador de soluções**.  
  
8.  Em **Solution Explorer**, escolha o nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
9. Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
10. No **modelos** painel, escolha o **definição de Site** modelo, deixe o **nome** como **SiteDefinition1**e, em seguida, escolha o  **Adicionar** botão.  
  
## <a name="create-a-visual-web-part"></a>Criar uma Web Part Visual  
 Em seguida, crie uma Web part visual para aparecer na página principal da definição de site.  
  
#### <a name="to-create-a-visual-web-part"></a>Para criar uma Web part visual  
  
1.  Em **Solution Explorer**, escolha o **Mostrar todos os arquivos** botão.  
  
2.  Escolha o **SiteDefinition1** nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
     A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
3.  Expanda o **Visual C#** nó ou o **Visual Basic** nó, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
4.  Na lista de modelos, escolha o **Web Part Visual** modelo, mantenha o padrão nome VisualWebPart1 e, em seguida, escolha o **adicionar** botão.  
  
     O arquivo VisualWebPart1.ascx é aberto.  
  
5.  Na parte inferior da VisualWebPart1.ascx, adicione a seguinte marcação para adicionar três controles ao formulário: uma caixa de texto, um botão e um rótulo:  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  Em VisualWebPart1.ascx, abra o arquivo VisualWebPart1.ascx.cs (para [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) ou VisualWebPart1.ascx.vb (para [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) e, em seguida, adicione o seguinte código:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Esse código adiciona a funcionalidade de clique do botão da web part.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Adicionar a Web Part Visual à Página ASPX Padrão  
 Em seguida, adicione a Web part visual para a página ASPX página de definição de site padrão.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Para adicionar uma Web part visual à página ASPX padrão  
  
1.  Abra a página de default.aspx e, em seguida, adicione a seguinte linha sob o `WebPartPages` marca:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Essa linha associa o nome MyWebPartControls a Web part e seu código. O *Namespace* parâmetro corresponda ao namespace que é usado no arquivo de código VisualWebPart1.ascx.  
  
2.  Após o `</asp:Content>` elemento, substitua todo o `ContentPlaceHolderId="PlaceHolderMain"` seção e seu conteúdo com o código a seguir:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Esse código cria uma referência para a Web part visual que você criou anteriormente.  
  
3.  Em **Solution Explorer**, abra o menu de atalho para o **SiteDefinition1** nó e, em seguida, escolha **definir como Item de inicialização**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Implantar e Executar a Solução de Definição do Site  
 Em seguida, implantar o projeto do SharePoint e, em seguida, execute o projeto.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Para implantar e executar a definição do site  
  
-   Na barra de menus, escolha **criar**, **TestSiteDef implantar**.  
  
-   Pressione a tecla F5.  
  
     O Visual Studio compila o código, adiciona seus recursos, todos os arquivos de pacotes em um arquivo de solução (WSP) do SharePoint e implanta o arquivo WSP SharePoint Server. SharePoint, em seguida, instala os arquivos e, em seguida, ativa os recursos.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Criar um Site com Base na Definição do Site  
 Em seguida, crie um site usando a nova definição de site.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Para criar um site usando a definição do site  
  
1.  No site do SharePoint, é exibida a página Novo Site do SharePoint.  
  
2.  No **título e descrição** seção, digite **meu novo Site** para o título e uma descrição do site.  
  
3.  No **endereço do Site** seção, digite **mynewsite** no **nome da URL** caixa.  
  
4.  No **modelo** , escolha o **SharePoint personalizações** guia.  
  
5.  No **selecionar um modelo de** , escolha **SiteDefinition1**.  
  
6.  Deixe as outras configurações em seus valores padrão e, em seguida, escolha o **criar** botão.  
  
     O novo site é exibido.  
  
## <a name="test-the-new-site"></a>Testar o Novo Site  
 Em seguida, teste o novo site para verificar se ele funciona corretamente.  
  
#### <a name="to-test-the-new-site"></a>Para testar o novo site  
  
-   Na página ASPX padrão, digite algum texto e, em seguida, escolha o **alterar o texto de rótulo** botão ao lado da caixa de texto.  
  
     O texto é exibido no rótulo à direita do botão.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  