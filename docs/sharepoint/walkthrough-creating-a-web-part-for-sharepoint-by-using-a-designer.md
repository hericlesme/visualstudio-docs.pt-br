---
title: 'Passo a passo: Criando um Web Part do SharePoint usando um Designer | Microsoft Docs'
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 28be854f01234783ff9873753eb88ca92bc192d6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>Instruções passo a passo: criando um Web Part do SharePoint usando um designer
  Se você criar web parts para um site do SharePoint, os usuários podem modificar diretamente o conteúdo, a aparência e o comportamento das páginas no site usando um navegador. Este passo a passo mostra como criar uma web part visualmente usando o SharePoint **Web Part Visual** modelo de projeto em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 A web part que você criará exibe um modo de exibição de calendário mensal e uma caixa de seleção para cada lista de calendário no site. Os usuários podem especificar qual calendário lista para incluir na exibição de calendário mensal marcando as caixas de seleção.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criar uma web part usando a **Web Part Visual** modelo de projeto.  
  
-   Criando a web part usando o designer Visual Web Developer no Visual Studio.  
  
-   Adicionando código para manipular os eventos dos controles na web part.  
  
-   Testando a web part no SharePoint.  
  
    > [!NOTE]  
    >  Seu computador pode mostrar diferentes nomes ou locais para alguns elementos da interface do usuário para o Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Windows e do SharePoint. Consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]ou superior.  
  
## <a name="creating-a-web-part-project"></a>Criando um projeto de web part  
 Primeiro, crie um projeto de web part usando a **Web Part Visual** modelo de projeto.  
  
#### <a name="to-create-a-visual-web-part-project"></a>Para criar um projeto de Web Part Visual  
  
1.  Iniciar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando o **executar como administrador** opção.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é exibida.  
  
3.  No **novo projeto** caixa de diálogo, em um **Visual C#** ou **Visual Basic**, expanda **Office/SharePoint**e, em seguida, escolha o  **Soluções do SharePoint** categoria.  
  
4.  Na lista de modelos, escolha o **SharePoint 2013 - Web Part Visual** modelo e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida. Usando este assistente, você pode especificar o site que você usará para depurar o projeto e o nível de confiança da solução.  
  
5.  No **o que é o nível de confiança para essa solução do SharePoint?** , escolha o **implantar como uma solução de farm** botão de opção.  
  
6.  Escolha o **concluir** botão para aceitar o site padrão local do SharePoint.  
  
## <a name="designing-the-web-part"></a>Criando a web part  
 Adicionando controles a partir de design a web part de **caixa de ferramentas** para a superfície de designer do Visual Web Developer.  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>Para criar o layout da web part  
  
1.  O designer Visual Web Developer, escolha o **Design** tab para alternar para modo de Design.  
  
2.  Na barra de menus, escolha **Exibir**, **Caixa de Ferramentas**.  
  
3.  No **padrão** nó do **caixa de ferramentas**, escolha o **CheckBoxList** controle e, em seguida, execute uma das seguintes etapas:  
  
    -   Abra o menu de atalho para o **CheckBoxList** de controle, escolha **cópia**, abra o menu de atalho para a primeira linha no designer e, em seguida, escolha **colar**.  
  
    -   Arraste o **CheckBoxList** controlar do **caixa de ferramentas**e conecte-se o controle para a primeira linha no designer.  
  
4.  Repita a etapa anterior, mas um botão Mover para a próxima linha do designer.  
  
5.  No designer, escolha o **Button1** botão.  
  
6.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
     O **propriedades** janela será aberta.  
  
7.  No **texto** propriedade do botão, digite **atualização**.  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>Manipulação de eventos de controles da web part  
 Adicione o código que permite que o usuário adicione calendários para o modo de exibição do calendário principal.  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>Para tratar eventos de controles da web part  
  
1.  Realize um dos seguintes conjuntos de etapas:  
  
    -   No designer, clique duas vezes o **atualização** botão.  
  
    -   No **propriedades** janela para o **atualização** botão, escolha o **eventos** botão. No **clique** propriedade, digite **Button1_Click**e, em seguida, escolha a tecla Enter.  
  
     O arquivo de código de controle de usuário é aberto no Editor de código e o `Button1_Click` manipulador de eventos é exibida. Posteriormente, você adicionará código para este manipulador de eventos.  
  
2.  Adicione as seguintes instruções para a parte superior do arquivo de código de controle de usuário.  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  Adicione a seguinte linha de código para o `VisualWebPart1` classe. Esse código declara um controle de exibição de calendário mensal.  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  Substitua o `Page_Load` método o `VisualWebPart1` classe com o código a seguir. Esse código executa as seguintes tarefas:  
  
    -   Adiciona uma exibição de calendário mensal para o controle de usuário.  
  
    -   Adiciona uma caixa de seleção para cada lista de calendário no site.  
  
    -   Especifica um modelo para cada tipo de item que aparece na exibição do calendário.  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  Substitua o `Button1_Click` método o `VisualWebPart1` classe com o código a seguir. Esse código adiciona itens de cada calendário selecionado para o modo de exibição do calendário principal.  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>Testar a web part  
 Quando você executar o projeto, abre o site do SharePoint. A web part é automaticamente adicionada à Galeria de Web Parts do SharePoint. Para testar este projeto, você executará as seguintes tarefas:  
  
-   Adicione um evento para cada uma das duas listas de calendário separado.  
  
-   Adicione a web part a uma página de web part.  
  
-   Especifique a lista para incluir na exibição de calendário mensal.  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Para adicionar eventos à lista de calendário no site  
  
1.  No Visual Studio, pressione a tecla F5.  
  
     Abre o site do SharePoint e o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] barra Início rápido é exibido na página.  
  
2.  Na barra Início rápido, sob **lista**, escolha o **calendário** link.  
  
     O **calendário** página será exibida.  
  
     Se você nenhum link de calendário é exibido na barra Início rápido, escolha o **o conteúdo do Site** link. Se a página de conteúdo do Site não mostrar um **calendário** item, crie um.  
  
3.  Na página do calendário, escolha um dia e, em seguida, escolha o **adicionar** link no dia selecionado para adicionar um evento.  
  
4.  No **título** , digite **evento no calendário padrão**e, em seguida, escolha o **salvar** botão.  
  
5.  Escolha o **o conteúdo do Site** link e, em seguida, escolha o **adicionar um aplicativo** lado a lado.  
  
6.  No **criar** página, escolha o **calendário** tipo, nome do calendário e, em seguida, escolha o **criar** botão.  
  
7.  Adicionar um evento para o novo calendário, nomeie o evento **evento no calendário personalizado**e, em seguida, escolha o **salvar** botão.  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>Para adicionar a web part a uma página de web part  
  
1.  Sobre o **o conteúdo do Site** página, abra o **páginas do Site** pasta.  
  
2.  Na faixa de opções, escolha o **arquivos** guia, abra o **novo documento** menu e, em seguida, escolha o **página de Web Part** comando.  
  
3.  Sobre o **nova página de Web Part** página, nomeie a página **SampleWebPartPage.aspx**e, em seguida, escolha o **criar** botão.  
  
     Página de web part é exibida.  
  
4.  Na área superior da página de web parts, escolha o **inserir** guia e, em seguida, escolha o **Web Part** botão.  
  
5.  Escolha o **personalizado** pasta, escolha o **VisualWebPart1** da web part e, em seguida, escolha o **adicionar** botão.  
  
     A web part aparece na página. Os seguintes controles aparecem na web part:  
  
    -   Um modo de exibição de calendário mensal.  
  
    -   Um **atualização** botão.  
  
    -   Um **calendário** caixa de seleção.  
  
    -   Um **calendário personalizado** caixa de seleção.  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Para especificar a lista para incluir na exibição de calendário mensal  
  
1.  Na web part, especificar calendários que você deseja incluir na exibição de calendário mensal e, em seguida, escolha o **atualização** botão.  
  
     Eventos de todos os calendários que você especificou aparecem na exibição de calendário mensal.  
  
## <a name="see-also"></a>Consulte também  
 [Criando Web Parts do SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Como: criar uma Web Part do SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Como: criar uma Web Part do SharePoint usando um Designer](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Instruções passo a passo: criando um Web Part para o SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  