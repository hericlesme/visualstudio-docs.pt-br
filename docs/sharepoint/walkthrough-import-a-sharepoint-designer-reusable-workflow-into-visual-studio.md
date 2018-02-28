---
title: "Passo a passo: Importar um fluxo de trabalho reutilizável do Designer do SharePoint no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 05428f2e702643b88415663249e9f29a9f7d46bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Informações passo a passo: importar um fluxo de trabalho reutilizável do designer do SharePoint para o Visual Studio
  Este passo a passo demonstra como importar um fluxo de trabalho reutilizável criado no SharePoint Designer 2010 em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto de fluxo de trabalho do SharePoint.  
  
 Fluxos de trabalho criados no SharePoint Designer, ou *fluxos de trabalho declarativos*, consistem em [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instruções em vez de código. O SharePoint Designer 2010 introduz *fluxos de trabalho reutilizáveis*, que são portáteis declarativos fluxos de trabalho que podem ser usados por listas diferentes em sites do SharePoint.  
  
 Fluxos de trabalho criados no [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], como fluxos de trabalho de máquina de estado e não sequenciais, são chamados *fluxos de trabalho de código*. Fluxos de trabalho de código consistem em arquivos XML e os módulos de código em que os usuários podem personalizar o comportamento do fluxo de trabalho.  
  
 O Visual Studio permite que você importar fluxos de trabalho reutilizáveis criados no SharePoint Designer 2010 e convertê-las em fluxos de trabalho de código para uso em seus sites do SharePoint.  
  
 Este passo a passo demonstra as seguintes tarefas:  
  
-   Criando um simple fluxo de trabalho reutilizável no SharePoint Designer.  
  
-   Exportar o fluxo de trabalho reutilizável do SharePoint Designer para um arquivo. wsp e no SharePoint.  
  
-   Importar o arquivo. wsp em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando o projeto de fluxo de trabalho reutilizável de importação.  
  
-   Alterando o fluxo de trabalho, adicionando o código.  
  
-   Usando o fluxo de trabalho importado em um site do SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições do [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Criar Subsites do SharePoint de Destino  
 Primeiro crie dois novos subsites do SharePoint: um para hospedar fluxos de trabalho reutilizáveis do SharePoint Designer, outro para hospedar fluxos de trabalho convertidos.  
  
#### <a name="to-create-sharepoint-subsites"></a>Para criar subsites do SharePoint  
  
1.  No SharePoint Designer 2010, na barra de menus, escolha **arquivo**, **novo Site da Web em branco**.  
  
2.  No **novo Site da Web em branco** caixa de diálogo, navegue até um site do SharePoint onde você deseja criar o fluxo de trabalho, ou usar o valor de http://*SystemName*/ e, em seguida, escolha o **Okey** botão.  
  
     A Home page é exibida.  
  
3.  No **Subsites** , escolha o **novo** botão.  
  
4.  No **novo** caixa de diálogo caixa, escolha **modelos do SharePoint** da lista no painel esquerdo e escolha **Site de equipe** da lista no painel direito.  
  
5.  No **especificar o local do site da Web** caixa, substitua a palavra **subsite** na URL com **SPD1**e, em seguida, escolha o **Okey** botão.  
  
     Isso abre o novo subsite no SharePoint Designer. Feche esta instância do SharePoint Designer e volte para a primeira instância (site de nível superior).  
  
6.  Repita as etapas de 3 a 5 para criar o segundo subsite, desta vez, substituindo a palavra **subsite** no [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] com **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Criar um Fluxo de Trabalho Reutilizável do SharePoint Designer  
 Como o SharePoint não inclui quaisquer fluxos de trabalho reutilizáveis que você pode usar para este exemplo, você criará um. Nesse fluxo de trabalho simples, quando um usuário insere uma nova tarefa na lista de tarefas que tem um título específico, a tarefa é atribuída a esse usuário.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Para criar um fluxo de trabalho reutilizável do SharePoint Designer  
  
1.  No **Subsites** , escolha o **SPD1** site modificá-lo.  
  
2.  Na faixa de opções, escolha o **fluxo de trabalho reutilizável** botão.  
  
     O assistente criar fluxo de trabalho reutilizável é exibido.  
  
3.  No **nome** , digite **fluxo de trabalho de tarefa SPD**.  
  
4.  No **tipo de conteúdo** , escolha **tarefa**e, em seguida, escolha o **Okey** botão.  
  
     O fluxo de trabalho é aberto no designer de fluxo de trabalho do SharePoint Designer.  
  
5.  No designer de fluxo de trabalho, escolha a etapa 1 e, em seguida, na faixa de opções, escolha o **condição** botão.  
  
6.  Na lista de condições, escolha **se campo do item atual for igual ao valor**.  
  
     Esta etapa adiciona uma condição chamada **se o campo de valor igual a**.  
  
7.  No **se o campo de valor igual a** condição, escolha o **campo** link.  
  
8.  Na lista de valores, escolha **título**.  
  
9. No **se o campo de valor igual a** condição, escolha o **valor** link.  
  
10. Na caixa, digite **nova tarefa**.  
  
     A instrução de condição agora lê **se atual: título do Item é igual a nova tarefa**.  
  
11. Escolha a linha em que a instrução de condição e, em seguida, na faixa de opções, escolha o **ação** botão.  
  
12. Na lista de ações, escolha **conjunto de campo no item atual**.  
  
13. No **campo do conjunto de valor** ação, escolha o **campo** link e, em seguida, na lista, escolha **atribuído a**.  
  
14. No **campo do conjunto de valor** ação, escolha o **valor** link e, em seguida, na lista de grupos e usuários existentes, escolha **usuário que criou o item**.  
  
15. Escolha o **adicionar** botão e, em seguida, escolha o **Okey** botão.  
  
     A instrução de ação agora lê **definir atribuído para a atual Item: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Salvar e Implantar o Fluxo de Trabalho Reutilizável  
 Porque [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pode importar somente os arquivos. wsp, você deve salvar o fluxo de trabalho reutilizável como um arquivo. wsp e implantá-lo no SharePoint antes de importá-lo em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Se você receber um erro de tempo de execução executar o procedimento a seguir, você precisa executar o procedimento em um sistema que tem acesso ao site do SharePoint.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Para salvar e implantar o fluxo de trabalho reutilizável  
  
1.  Na parte superior do Designer do SharePoint, escolha o **salvar** botão para salvar seu progresso e, em seguida, escolha o **publicar** botão implantar o fluxo de trabalho para o **SPD1** site do SharePoint .  
  
2.  No painel de navegação, escolha o **fluxos de trabalho** objeto.  
  
3.  Em **fluxo de trabalho reutilizável**, escolha **fluxo de trabalho de tarefa SPD**.  
  
4.  Na faixa de opções, escolha o **Salvar como modelo** botão para salvar o fluxo de trabalho como um arquivo. wsp.  
  
5.  Abra o **SPD1** site do SharePoint em um navegador para exibir o arquivo. wsp no SharePoint.  
  
6.  Na barra de início rápido, escolha o **bibliotecas** link.  
  
7.  No **bibliotecas de documentos** , escolha o **ativos do Site** link.  
  
     O **fluxo de trabalho de tarefa SPD** arquivo está listado com outros ativos de site.  
  
8.  Na lista de arquivos, escolha o nome do arquivo  
  
9. No **Download de arquivo** caixa de diálogo caixa, escolha o **salvar** botão para salvar o arquivo. wsp em seu sistema local.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Importar o Arquivo .wsp no Visual Studio  
 Importar o arquivo. wsp para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando um projeto de fluxo de trabalho reutilizável de importação. Este projeto converte o fluxo de trabalho de um fluxo de trabalho reutilizável, declarativo em um fluxo de trabalho de código. Depois que o fluxo de trabalho é convertido, você usará o código para modificar seu comportamento.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Para importar um fluxo de trabalho a partir de um arquivo .wsp e modificá-lo  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
3.  No **modelos** painel, escolha o **fluxo de trabalho de importação reutilizável do SharePoint 2010** modelo, deixe o nome do projeto como **WorkflowImportProject1**e, em seguida, escolha o **Okey** botão.  
  
     O Assistente de personalização do SharePoint é exibida.  
  
4.  No **especificar o nível de site e segurança de depuração** , insira o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para o segundo subsite do SharePoint que você criou anteriormente: http://*nome de sistema*/SPD2.  
  
5.  No **o que é o nível de confiança para essa solução do SharePoint?** , escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **próximo** botão.  
  
     Para obter mais informações sobre a área restrita em comparação com soluções de farm, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  No **especificar a nova fonte de projeto** página, navegue até o local no sistema onde você salvou o arquivo. wsp anteriormente, abra o arquivo e, em seguida, escolha o **próximo** botão.  
  
    > [!NOTE]  
    >  Escolha o **concluir** botão Importar todos os itens disponíveis no arquivo. wsp.  
  
     Isso exibe uma lista de fluxos de trabalho reutilizáveis disponíveis para importação.  
  
7.  No **selecionar itens para importar** caixa, escolha o **fluxo de trabalho de tarefa SPD** fluxo de trabalho e, em seguida, escolha o **concluir** botão.  
  
     Depois que a operação de importação for concluída, um projeto chamado **WorkflowImportProject1** é criado contendo um fluxo de trabalho chamado **SPD_Workflow_TestFT**. Nessa pasta é o arquivo de definição do fluxo de trabalho Elements. XML e o arquivo de designer de fluxo de trabalho (. xoml). O designer contém dois arquivos: o arquivo de regras (. Rules) e o arquivo code-behind (. cs ou. vb, dependendo da linguagem de programação do projeto).  
  
8.  Em **Solution Explorer**, exclua o **outros arquivos importados** pasta.  
  
9. No arquivo Elements, exclua `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. Em **Solution Explorer**, escolha **WorkflowImportProject1**e, em seguida, na barra de menus, escolha **projeto**, **definir como projeto de inicialização** para definir **WorkflowImportProject1** como o Item de inicialização.  
  
     Isso exibe a lista imediatamente quando você depura o projeto.  
  
11. Porque o **importar do SharePoint 2010 fluxo de trabalho reutilizável** modelo não importa os valores de propriedade de associação do fluxo de trabalho importados, você deve inseri-los. Para fazer isso:  
  
    1.  Em **Solution Explorer**, escolha o **SPD_Workflow_TestFT** nó.  
  
    2.  Escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) botão ao lado de uma lista de propriedades, como o **lista de destino** propriedade.  
  
    3.  Preencha os valores ausentes no Assistente de personalização do SharePoint e, em seguida, escolha o **concluir** botão.  
  
12. Escolha o arquivo. xoml e, em seguida, na barra de menus, escolha **exibição**, **Designer** para exibir o fluxo de trabalho importado no designer de fluxo de trabalho.  
  
13. No **v 3.0 do fluxo de trabalho do Windows** nó do **caixa de ferramentas**, execute uma das seguintes etapas:  
  
    -   Abra o menu de atalho para o **código** atividade e, em seguida, escolha **cópia**. No designer de fluxo de trabalho, abra o menu de atalho para a linha abaixo de **SequenceActivity1** atividade e, em seguida, escolha **colar**.  
  
    -   Arraste o **código** atividade do **caixa de ferramentas** para o designer de fluxo de trabalho e conecte-se para a linha no **SequenceActivity1** atividade.  
  
     Isso adicionará uma atividade para o designer de fluxo de trabalho chamado **CodeActivity1**. Nesta atividade, você adicionará uma ação de código que cria um comunicado da lista quando o usuário inicia o fluxo de trabalho.  
  
14. Realize um dos seguintes conjuntos de etapas:  
  
    -   Clique duas vezes em **CodeActivity1** para gerar um manipulador de eventos e exibir o código.  
  
    -   No **propriedades** janela para **CodeActivity1**, defina o valor da **ExecuteCode** propriedade **codeActivity_ExecuteCode**.  
  
15. Adicione o seguinte em existente **usando** ou **Imports** instruções:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Substituir `codeActivity1_ExecuteCode` com o seguinte:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Implantar o Projeto e Associar o Fluxo de Trabalho  
 Em seguida, execute WorkflowImportProject1 para implantá-lo em um site do SharePoint e, em seguida, associe o fluxo de trabalho com a lista de tarefas para visualizar e testar a modificação, convertida fluxo de trabalho.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Para implantar o projeto e associar o fluxo de trabalho  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], pressione a tecla F5 para executar e implantar o projeto de fluxo de trabalho convertido.  
  
2.  Na barra de início rápido, escolha o **tarefas** link para exibir a lista de tarefas.  
  
3.  No **lista ferramentas** guia, escolha o **itens** botão e, em seguida, escolha o **Novo Item** botão.  
  
     O **tarefas - Novo Item** caixa de diálogo é aberta.  
  
4.  No **título** , digite **nova tarefa**e, em seguida, escolha o **salvar** botão.  
  
5.  No **lista ferramentas** guia, escolha o **lista** botão e, em seguida, escolha o **as configurações da lista** botão.  
  
     O **as configurações da lista** página será exibida.  
  
6.  No **permissões e gerenciamento** , escolha o **configurações de fluxo de trabalho** link.  
  
     O **configurações de fluxo de trabalho** página será exibida.  
  
7.  Escolha o **adicionar um fluxo de trabalho** link.  
  
8.  No **fluxo de trabalho** , escolha **WorkflowImportProject1 - teste de fluxo de trabalho SPD**.  
  
9. No **nome** , digite **teste de fluxo de trabalho SPD**e, em seguida, escolha o **Okey** botão.  
  
10. Na barra de início rápido, escolha o **tarefas** lista.  
  
11. Clique na seta ao lado de **nova tarefa**e, em seguida, na lista, escolha **fluxos de trabalho**.  
  
12. No **iniciar um novo fluxo de trabalho** , escolha o link para **teste de fluxo de trabalho SPD**e, em seguida, escolha o **iniciar** botão para iniciar o fluxo de trabalho.  
  
    > [!NOTE]  
    >  Como alternativa, você pode autoassociar um fluxo de trabalho com uma lista executando o Assistente de configurações de fluxo de trabalho e definindo o fluxo de trabalho para associar automaticamente.  
  
     Observe que as duas ações são executadas pelo fluxo de trabalho: seu nome é exibido na tarefa de **atribuído a** coluna e um aviso é exibido no **anúncios** lista.  
  
## <a name="see-also"></a>Consulte também  
 [Importando itens de um Site do SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Criando controles reutilizáveis para Web Parts ou páginas de aplicativo](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  