---
title: 'Passo a passo: Importar itens de um Site do SharePoint existente | Microsoft Docs'
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b9d1bcc72bd22e7c528b2a3d8752d15b7005fea5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Instruções passo a passo: importar itens de um local do SharePoint existente
  Este passo a passo demonstra como importar itens de um site do SharePoint existente em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Personalizando um site do SharePoint, adicionando uma coluna de um site personalizado (também conhecido como um *campo*.  
  
-   Exportando um site do SharePoint para um arquivo. wsp.  
  
-   Importar o arquivo. wsp em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint usando o projeto de importação. wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições do [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="customizing-a-sharepoint-site"></a>Personalizando um Site do SharePoint  
 Neste exemplo, você criará e personalizar um subsite do SharePoint, adicionando uma nova coluna de site a ele e criar outro subsite para uso posterior. Posteriormente, você exportar o subsite primeiro em um arquivo. wsp e, em seguida, importar a coluna de site personalizado para o segundo subsite usando o projeto de importação. wsp.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Para criar e personalizar um site do SharePoint  
  
1.  Abrir um site do SharePoint usando um navegador da Web, como http://*nome de sistema*/SitePages/Home.aspx.  
  
2.  Criar um subsite fora do site do SharePoint principal abrindo o **ações do Site** menu e, em seguida, escolhendo **novo Site**.  
  
3.  O site **criar** caixa de diálogo caixa, escolha o **Site vazio** tipo.  
  
4.  No **título** , digite **Site coluna teste 1**; no **nome da URL** , digite **columntest1**; deixar as outras configurações no padrão valores; e, em seguida, escolha o **criar** botão.  
  
5.  Depois que o site for criado, navegue no navegador para o site principal, http://*nome de sistema*/SitePages/Home.aspx.  
  
6.  Novamente, crie um subsite em branco fora do site do SharePoint principal abrindo o **ações do Site** menu, escolhendo **novo Site**e, em seguida, escolhendo o **Site vazio** tipo.  
  
7.  No **título** , digite **teste 2 de coluna de Site**; no **nome da URL** , digite **columntest2**; deixar as outras configurações no padrão valores; e, em seguida, escolha o **criar** botão.  
  
8.  Navegue de volta para o primeiro subsite, http://*SystemName*/columntest1/default.aspx.  
  
9. Sobre o **ações do Site** menu, escolha **configurações de Site** para exibir a página de configurações do Site.  
  
10. No **galerias** , escolha o **Site colunas** link.  
  
11. Na parte superior do **Galeria da coluna de Site** página, escolha o **criar** botão.  
  
12. No **nome de coluna** , digite **coluna teste**, manter os outros valores padrão e, em seguida, escolha o **Okey** botão.  
  
13. O **coluna teste** coluna aparecerá nas colunas personalizadas título na Galeria de coluna de Site.  
  
## <a name="exporting-the-sharepoint-site"></a>Exportando o Site do SharePoint  
 Em seguida, obter um arquivo de instalação (. wsp) do SharePoint que contém os itens do SharePoint e os elementos que você deseja importar para seu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto do SharePoint. Se você ainda não tiver um arquivo. wsp, você deve criar um de um site do SharePoint existente. Neste exemplo, você exportará o site padrão do SharePoint em um arquivo. wsp.  
  
> [!IMPORTANT]  
>  Se você receber um erro de tempo de execução executar o procedimento a seguir, você precisa executar o procedimento em um sistema que tem acesso ao site do SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Para exportar um site do SharePoint existente  
  
1.  No site do SharePoint, escolha **configurações de Site** no **ações do Site** guia para exibir a página de configurações do Site.  
  
2.  No **ações do Site** seção da página Configurações de Site, escolha o **site Salvar como modelo** link.  
  
3.  No **nome de arquivo** , digite **ExampleSite**e no **nome do modelo** , digite **do Site de exemplo**.  
  
4.  Neste exemplo, deixe o **incluir conteúdo** caixa de seleção desmarcada.  
  
     Se você selecionar essa caixa, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] salva todas as listas e bibliotecas de documentos e seu conteúdo, o arquivo. wsp. Embora isso seja útil em algumas circunstâncias, não é necessário para este exemplo.  
  
5.  Quando a operação for concluída com êxito, escolha o **Galeria de soluções** link para exibir o arquivo. wsp.  
  
     Para exibir a página de galeria de soluções posterior, abra o **ações do Site** menu, escolha **configurações de Site**, escolha o **ir para configurações de site de nível superior** link no  **Site de administração do conjunto de** seção e, em seguida, escolha o **soluções** link no **galerias** seção.  
  
6.  Na Galeria de soluções, escolha o **ExampleSite** link.  
  
7.  No **Download de arquivo** caixa de diálogo caixa, escolha o **salvar** botão para salvar o arquivo em seu sistema local, por padrão, na sua pasta de Downloads.  
  
## <a name="importing-the-wsp-file"></a>Importar o arquivo. wsp  
 Agora que você tem um arquivo. wsp que contém um item que você deseja reutilizar (a coluna de site personalizado coluna teste), importe o arquivo. wsp para acessá-lo.  
  
#### <a name="to-import-a-wsp-file"></a>Para importar um arquivo. wsp  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na barra de menus, escolha **arquivo**, **novo**, **projeto** para exibir o **novo projeto** caixa de diálogo. Se seu IDE está definido para usar configurações de desenvolvimento do Visual Basic, na barra de menus, escolha **arquivo**, **novo projeto**.  
  
2.  Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
3.  Escolha o **Importar pacote de solução do SharePoint 2010** modelo o **modelos** painel, deixe o nome do projeto como WspImportProject1 e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
4.  No **especificar o nível de site e segurança de depuração** , insira o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para o segundo subsite do SharePoint que você criou anteriormente. Você adicionará personalizado novo campo de item, http://*nome do sistema*/columntest2 desse subsite.  
  
5.  No **o que é o nível de confiança para essa solução do SharePoint?** seção, deixe a seleção como **implantar como uma solução em área restrita**.  
  
6.  No **especificar a nova fonte de projeto** página, navegue até o local no sistema onde você salvou o arquivo. wsp anteriormente e, em seguida, escolha o **próximo** botão.  
  
    > [!NOTE]  
    >  Se você escolher o **concluir** botão nessa página, todos os itens disponíveis no arquivo. wsp será importado.  
  
7.  No **selecionar itens para importar** caixa, desmarque todas as caixas de seleção na lista exceto **coluna teste**e, em seguida, escolha o **concluir** botão.  
  
     Como a lista contém muitos itens, você pode escolher o Ctrl + uma chave para escolher todos os itens na lista, escolha a tecla de espaço para limpar todas as caixas de seleção e, em seguida, selecione a caixa de seleção ao lado de **coluna teste** item.  
  
     Depois que a operação de importação for concluída, um novo projeto denominado **WspImportProject1** é criado que contém uma pasta chamada **campos**. Essa pasta é a coluna de site personalizado **coluna teste** e seu arquivo de definição Elements.  
  
## <a name="deploying-the-project"></a>Implantar o projeto  
 Por fim, implantar **WspImportProject1** para o SharePoint segundo subsite que você criou anteriormente para exibir a coluna de site personalizado.  
  
#### <a name="to-deploy-the-project"></a>Para implantar o projeto  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], pressione a tecla F5 para implantar e executar o projeto de importação. wsp.  
  
2.  No site do SharePoint, abra o **ações do Site** menu e, em seguida, escolha **configurações de Site** para exibir a página de configurações do Site.  
  
3.  No **galerias** , escolha o **Site colunas** link.  
  
4.  Role para baixo até o **colunas personalizadas** seção.  
  
     Observe que a coluna de site personalizado que você importou o primeiro site do SharePoint é exibido na lista.  
  
## <a name="see-also"></a>Consulte também  
 [Importando itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  