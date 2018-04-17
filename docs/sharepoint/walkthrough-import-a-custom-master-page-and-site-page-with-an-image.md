---
title: 'Passo a passo: Importar página mestre personalizada e página com uma imagem do Site | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f90f85e7f22cf3bdecf90aaf6f8d61af3f399a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Instruções passo a passo: importar página mestre personalizada e página do local com uma imagem
  Este passo a passo demonstra como importar uma página mestre personalizada do SharePoint e uma página de site que tem uma imagem em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint.  
  
 Esta explicação passo a passo mostra como realizar as tarefas seguintes:  
  
-   Crie uma página mestre personalizada e uma página do site usando uma imagem no SharePoint Designer.  
  
-   Exporte uma página mestre personalizada, a imagem e a página do site para um arquivo de solução (. wsp) do SharePoint.  
  
-   Importar e implantar o arquivo. wsp em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint usando o projeto Importar pacote de solução do SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você deve ter os seguintes componentes para concluir este passo a passo:  
  
-   Edições do [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e do SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   O SharePoint Designer 2010.  
  
## <a name="create-items-in-sharepoint-designer"></a>Criar itens no SharePoint Designer  
 Este exemplo mostra como criar três itens no SharePoint Designer para exportação: uma página mestre personalizada, uma página de site que faz referência a página mestre personalizada e um arquivo de imagem para aparecer na página do site. A imagem é adicionada à pasta /images/ no SharePoint.  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Para criar uma página mestre personalizada no SharePoint Designer  
  
1.  No SharePoint Designer, no painel de navegação, escolha o **páginas mestras** objeto do site.  
  
2.  Sobre o **páginas mestras** de faixa de opções, escolha **página mestra em branco**.  
  
3.  Escolha a nova página mestra e, em seguida, no **páginas mestras** de faixa de opções, escolha **Editar arquivo**.  
  
4.  Na parte inferior do Designer do SharePoint, escolha o **código** guia.  
  
5.  Substitua a marcação existente com a seguinte marcação.  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  Salve a página, escolha o **páginas mestras** guia e renomeie a página mestra como **mybasic1.master**.  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Adicionar uma imagem para o banco de dados de conteúdo no SharePoint Designer  
 Agora você pode adicionar uma imagem a ser exibida na página do site. A imagem é implantada para o banco de dados de conteúdo do SharePoint.  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Para adicionar uma imagem para o banco de dados de conteúdo no SharePoint Designer  
  
1.  No painel de navegação, escolha o **todos os arquivos** objeto do site e, em seguida, na exibição de árvore, escolha o **imagens** pasta.  
  
2.  No **todos os arquivos** de faixa de opções, escolha **importar arquivos**, escolha um arquivo de sua escolha e, em seguida, escolha o **Okey** botão. Neste exemplo, o arquivo é nomeado **myimg1.png**.  
  
     Opcionalmente, você pode criar uma subpasta para ajudar a organizar as imagens.  
  
3.  Fechar o **importação** caixa de diálogo.  
  
## <a name="create-a-site-page"></a>Criar uma página do Site  
 Esta página de site básico usa a página mestre personalizada e exibe a imagem que você adicionou na etapa anterior.  
  
#### <a name="to-create-a-site-page"></a>Para criar uma página do site  
  
1.  No painel de navegação, escolha o **páginas do Site** objeto.  
  
2.  No **páginas** de faixa de opções, escolha o **página** botão, escolha o **ASPX** tipo de página e, em seguida, nomeie o novo arquivo **mycontentpage1.aspx**.  
  
     Opcionalmente, você pode criar uma subpasta para ajudar a organizar as páginas do site.  
  
3.  Na lista de páginas do site, escolha **MyContentPage1.aspx** para abrir sua página de propriedades e, em seguida, na parte inferior da página, escolha o **Editar arquivo** link.  
  
     Se uma mensagem é exibida e afirma que esta página não contém nenhuma região que seja editável no modo de segurança e perguntando se deseja abrir essa página no modo avançado, escolha o **Sim** botão.  
  
4.  Na parte inferior da página, escolha o **código** botão.  
  
5.  Substitua a marcação existente com a seguinte marcação.  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  Salve a página do site atualizado.  
  
## <a name="export-the-items-from-sharepoint"></a>Exportar os itens do SharePoint  
 Exporte os itens do SharePoint para um arquivo de solução (. wsp) do SharePoint.  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>Para exportar os itens do SharePoint Designer  
  
1.  No SharePoint Designer, no painel de navegação, escolha o **Site de equipe** objeto e, em seguida, o **Site** de faixa de opções, escolha **Salvar como modelo**.  
  
2.  No **Salvar como modelo** caixa de diálogo caixa, digite um nome de arquivo e o nome do modelo, selecione o **incluir conteúdo** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
     Isso salva o conteúdo do site no arquivo. wsp.  
  
3.  Depois de exporta a solução, escolha o **Galeria de soluções** link para exibir a lista de arquivos de solução disponível.  
  
4.  Abra o menu de atalho para o novo arquivo. wsp e, em seguida, escolha **Salvar destino como** para salvá-lo para o sistema.  
  
## <a name="import-the-items-into-visual-studio"></a>Importar os itens no Visual Studio  
 Importar o arquivo. wsp para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Depois de importar o conteúdo, pode personalizá-lo, adicionar mais itens e, em seguida, implantá-lo.  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Para importar itens de arquivo. wsp no Visual Studio  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], crie um **Importar pacote de solução do SharePoint 2010** projeto.  
  
2.  Sobre o **selecionar itens para importar** página em **módulo** no **tipo** coluna, marque as caixas de seleção para somente os arquivos na tabela a seguir para importar.  
  
    |Nome do Arquivo|Descrição|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|A página mestre personalizada.|  
    |images_|O arquivo de imagem no sistema de arquivos do SharePoint.|  
    |SitePages_|A página do site.|  
  
3.  Escolha o **concluir** botão Importar os itens selecionados.  
  
4.  Em **Solution Explorer**, escolha o _catalogsmasterpage\_ nó e defina o valor de seu **resolução de conflitos de implantação** propriedade **automática**.  
  
     Isso ajuda a garantir que qualquer conflito de implantação é resolvidos automaticamente.  
  
5.  Se a nova página mestra tem o mesmo nome de uma página existente, certifique-se de que a página existente não está marcada como uma página mestra padrão ou uma página mestre personalizada no SharePoint Designer.  
  
     Se uma página mestra existente é marcada como padrão o mestre de página ou página mestre personalizada, você obterá um erro de implantação que declara que a página mestra não pode ser excluída. Para evitar esse problema, faça o seguinte:  
  
    -   Se a página mestra existente for definida como padrão o mestre de página, defina outra página mestra temporariamente como página padrão de mestre. Depois de implantar os arquivos do SharePoint, defina a nova página mestra como padrão o mestre de página.  
  
    -   Se a página mestra existente for definida como página mestre personalizada, defina outra página mestra temporariamente como página mestre personalizada. Depois de implantar os arquivos do SharePoint, defina a nova página mestra como página mestre personalizada.  
  
6.  Na barra de menus, escolha **criar**, **implantar solução**.  
  
7.  Abra o site do SharePoint para exibir os itens implantados.  
  
 Uma maneira alternativa para importar arquivos para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e implantá-los para o SharePoint é para adicionar os arquivos em módulos no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Como: importar uma página mestre ou tema](../sharepoint/how-to-import-a-master-page-or-theme.md) e [usando módulos para incluir arquivos na solução](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Importando itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  