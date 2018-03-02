---
title: "Passo a passo: Implantando uma definição de lista de tarefas do projeto | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: cae6b4590c2bb0382b1ff46af51e9c79dfdd9c0e
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Passo a passo: Implantando uma definição de lista de tarefas de projeto

Este passo a passo mostra como usar [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] para criar, personalizar, depurar e implantar uma lista do SharePoint para controlar as tarefas do projeto.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Pré-requisitos

- Edições com suporte do Microsoft Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- 2017 do Visual Studio ou uma edição do Visual Studio aplicativo Lifecycle Management (ALM).

## <a name="CreatingListDef"></a> Criando uma lista do SharePoint

Crie um projeto de lista do SharePoint e associar a definição de lista de tarefas.

1. Abra o **novo projeto** caixa de diálogo caixa, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.

2. No **modelos** painel, escolha o **projeto do SharePoint 2010** modelo, nomeie o projeto **ProjectTaskList**e, em seguida, escolha o **Okey**botão.

     O **Assistente de personalização do SharePoint** é exibida.

3. Especifique o site do SharePoint local que você pode usar para depuração, escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **concluir** botão.

4. Abra o menu de atalho para o projeto e, em seguida, escolha **adicionar**, **Novo Item**.

5. No **modelos** painel, escolha o **lista** modelo e, em seguida, escolha o **adicionar** botão.

     O **Assistente de personalização do SharePoint** é exibida.

6. No **que nome você deseja exibir para sua lista?** , digite **lista de tarefas de projeto**.

7. Escolha o **criar uma lista não é personalizável com base em um tipo de lista existente de** botão de opção e, em seguida, na lista, escolha **tarefas**e, em seguida, escolha o **concluir** botão.

     A lista, recurso e pacote aparecem na **Gerenciador de soluções**.

## <a name="AddEventRcvr"></a> Adicionando um receptor de evento

Na lista de tarefas, você pode adicionar um receptor de evento que define automaticamente o vencimento Data e a descrição da tarefa. O procedimento a seguir adiciona um manipulador de eventos simples para a instância de lista como um receptor de evento.

1. Abra o menu de atalho para o nó do projeto, escolha **adicionar**e, em seguida, escolha **Novo Item**.

2. Na lista de modelos do SharePoint, escolha o **receptor de evento** modelo e, em seguida, nomeie- **ProjectTaskListEventReceiver**.

     O **Assistente de personalização do SharePoint** é exibida.

3. No **escolha configurações de receptor de evento** escolha **eventos de Item de lista** como o tipo de receptor de evento no **que tipo de receptor de eventos você deseja** lista.

4. No **o item deve ser a origem do evento** , escolha **tarefas**.

5. Na lista de eventos para manipular, marque a caixa de seleção ao lado **um item foi adicionado**e, em seguida, escolha o **concluir** botão.

     Um novo nó de receptor de evento é adicionado ao projeto com um arquivo de código que é chamado **ProjectTaskListEventReceiver**.

6. Adicione código para o `ItemAdded` método o **ProjectTaskListEventReceiver** arquivo de código. Cada vez que uma nova tarefa é adicionada, um padrão de data de vencimento e uma descrição é adicionado à tarefa. O padrão devido a data é 1º de julho de 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="CustomizeFeature"></a> Personalizando o recurso de lista de tarefas de projeto

Quando você cria uma solução do SharePoint, o Visual Studio cria automaticamente os recursos para o padrão itens de projeto. Você pode personalizar as configurações de lista de tarefas do projeto para o site do SharePoint usando o Designer de recursos.

1. Em **Solution Explorer**, expanda **recursos**.

2. Abra o menu de atalho para **Feature1**e, em seguida, escolha **Designer de exibição**.

3. No **título** , digite **recurso de lista de tarefas de projeto**.

4. No **escopo** , escolha **Web**.

5. No **propriedades** janela, digite **1.0.0.0** como o valor para o **versão** propriedade.

## <a name="CustomizePackage"></a> Personalizando o pacote de lista de tarefas de projeto

Quando você cria um projeto do SharePoint, o Visual Studio adiciona automaticamente os recursos que contêm os itens de projeto padrão para o pacote. Você pode personalizar as configurações de lista de tarefas do projeto para o site do SharePoint usando o Designer de pacote.

1. Em **SolutionExplorer**, abra o menu de atalho para **pacote**e, em seguida, escolha **Designer de exibição**.

2. No **nome** , digite **ProjectTaskListPackage**.

3. Selecione o **redefinir o servidor de Web** caixa de seleção.

## <a name="BuildTest"></a> Compilar e testar a lista de tarefas de projeto

Quando você executar o projeto, abre o site do SharePoint. No entanto, você deve navegar manualmente para o local da lista de tarefas.

1. Escolha a tecla F5 para compilar e implantar sua lista de tarefas do projeto.

     Abre o site do SharePoint.

2. Escolha o **início** guia.

3. Na barra lateral esquerda, escolha o **lista de tarefas de projeto** link.

     A página de lista de tarefas de projeto é exibida.

4. No **lista ferramentas** guia, escolha o **itens** guia.

5. No **itens** de grupo, escolha o **Novo Item** botão.

6. No **título** texto, digite **Task1**.

7. Escolha o **salvar** botão.

     Depois que o site for atualizado, o **Task1** tarefa é exibida com uma data de vencimento de 1/7/2009.

8. Escolha **Task1**.

     A exibição detalhada da tarefa é exibida e a descrição mostra "É uma tarefa crítica."

## <a name="Deploy"></a> Implantando a lista de tarefas de projeto

Depois de criar e testar a lista de tarefas do projeto, você pode implantá-lo para o *sistema local* ou um *sistema remoto*. O sistema local é o mesmo computador em que você desenvolveu a solução, enquanto um sistema remoto é um computador diferente.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Para implantar a lista de tarefas de projeto para o sistema local

Na barra de menus do Visual Studio, escolha **criar**, **implantar solução**.

O Visual Studio recicla o pool de aplicativos do IIS, cancela todas as versões existentes da solução, copia o arquivo de pacote (. wsp) da solução do SharePoint e ativa seus recursos. Agora você pode usar a solução no SharePoint. Para obter mais informações sobre as etapas de configuração de implantação, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Para implantar a lista de tarefas do projeto em um sistema remoto

1. Na barra de menus do Visual Studio, escolha **criar**, **publicar**.

2. No **publicar** caixa de diálogo caixa, escolha o **publicar no sistema de arquivos** botão de opção.

     Você pode alterar o local de destino no **publicar** caixa de diálogo, escolhendo o botão de reticências ![ícone de reticências](../sharepoint/media/ellipsisicon.gif "ícone de reticências") e, em seguida, navegar para outro local.

3. Escolha o **publicar** botão.

     Um arquivo. wsp é criado para a solução.

4. Copie o arquivo. wsp ao sistema remoto do SharePoint.

5. Use o PowerShell `Add-SPUserSolution` comando para instalar o pacote de instalação remota do SharePoint. (Para soluções de farm, use o `Add-SPSolution` comando.)

     Por exemplo, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Use o PowerShell `Install-SPUserSolution` comando para implantar a solução. (Para soluções de farm, use o `Install-SPSolution` comando.)

     Por exemplo, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Para obter mais informações sobre implantação remota, consulte [usando soluções](http://go.microsoft.com/fwlink/?LinkId=217680) e [adicionando e implantando soluções com o PowerShell no SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Próximas etapas

Você pode aprender mais sobre como personalizar e implantar soluções do SharePoint os seguintes tópicos:

- [Instruções passo a passo: criar uma coluna de site, tipos de conteúdo e listas para o SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Como criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell para o SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Consulte também

[Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)