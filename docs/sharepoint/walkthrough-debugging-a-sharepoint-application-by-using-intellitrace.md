---
title: 'Passo a passo: Depurando um aplicativo do SharePoint usando o IntelliTrace | Microsoft Docs'
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
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: d9f3e5ae5997f7ae4f7c7f94bc61dc526404f144
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>Instruções passo a passo: depurando um aplicativo do SharePoint usando o IntelliTrace

Usando o IntelliTrace, você pode depurar mais facilmente soluções do SharePoint. Depuradores tradicionais fornecem apenas um instantâneo de uma solução no momento atual. No entanto, você pode usar o IntelliTrace para examinar os eventos que ocorreram na sua solução e o contexto em que ocorreu e navegue até o código.

 Este passo a passo demonstra como depurar um projeto do SharePoint 2010 ou SharePoint 2013 no Visual Studio usando o Microsoft Monitoring Agent para coletar dados do IntelliTrace de aplicativos implantados. Para analisar os dados, você deve usar o Visual Studio Enterprise. Este projeto incorpora um receptor de recursos que, quando o recurso está ativado, adiciona uma tarefa à lista de tarefas e um anúncio para a lista de avisos. Quando o recurso for desativado, a tarefa é marcada como concluída, e um segundo aviso é adicionado à lista de anúncios. No entanto, o procedimento contém um erro de lógico que impede que o projeto sendo executado corretamente. Usando o IntelliTrace, você localizar e corrigir o erro.

 **Aplica-se a:** as informações neste tópico se aplicam a soluções do SharePoint 2010 e SharePoint 2013 que foram criadas no Visual Studio.

 Esta explicação passo a passo ilustra as seguintes tarefas:

- [Criar um receptor de recursos](#BKMK_CreateReceiver)

- [Adicione código para o receptor de recursos](#BKMK_AddCode)

- [O projeto de teste](#BKMK_Test1)

- [Coletar dados do IntelliTrace usando o Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Depurar e corrigir a solução do SharePoint](#BKMK_DebugSolution)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Edições com suporte do Windows e do SharePoint. Consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Visual Studio Enterprise.

## <a name="BKMK_CreateReceiver">Criar um receptor de recursos</a>

Primeiro, crie um projeto vazio do SharePoint que tem um receptor de recursos.

1. Crie um projeto de solução do SharePoint 2010 ou SharePoint 2013 e nomeie- **IntelliTraceTest**.

     O **Assistente de personalização do SharePoint** for exibida, na qual você pode especificar o site do SharePoint para o projeto e o nível de confiança da solução.

2. Escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **concluir** botão.

     IntelliTrace funciona apenas em soluções de farm.

3. Em **Solution Explorer**, abra o menu de atalho para o **recursos** nó e, em seguida, escolha **adicionar recurso**.

     Feature1.Feature é exibida.

4. Abra o menu de atalho para Feature1.feature e, em seguida, escolha **adicionar receptor de evento** para adicionar um módulo de código para o recurso.

## <a name="BKMK_AddCode">Adicione código para o receptor de recursos</a>

Em seguida, adicione código para dois métodos no receptor de recursos: `FeatureActivated` e `FeatureDeactivating`. Esses métodos disparam sempre que um recurso é ativado ou desativado no SharePoint, respectivamente.

1. Na parte superior do `Feature1EventReceiver` classe, adicione o código a seguir, que declara variáveis que especifique o site do SharePoint e do subsite:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Substitua o método `FeatureActivated` pelo seguinte código:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Substitua o método `FeatureDeactivating` pelo seguinte código:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!"); 
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="BKMK_Test1">O projeto de teste</a>

Agora que o código é adicionado para o receptor e o coletor de dados está em execução, implantar e executar a solução do SharePoint para testar se ele funciona corretamente.

> [!IMPORTANT]
> Neste exemplo, um erro será lançado no manipulador de eventos FeatureDeactivating. Posteriormente neste passo a passo, você pode localizar esse erro usando o arquivo. itrace que criou o coletor de dados.

1. Implantar a solução do SharePoint e, em seguida, abra o site do SharePoint em um navegador.

     O recurso ativa automaticamente, fazendo com que seu destinatário de recurso Adicionar um aviso e uma tarefa.

2. Exiba o conteúdo das listas de tarefas e anúncios.

     A lista de avisos deve ter um novo anúncio chamado **recurso ativado: IntelliTraceTest_Feature1**, e a lista de tarefas deve ter uma nova tarefa é denominada **Desativar recurso: IntelliTraceTest_ Feature1**. Se qualquer um desses itens estiver ausente, verifique se o recurso está ativado. Se ele não estiver ativado, ative-o.

3. Desative o recurso executando as seguintes etapas:

    1. Sobre o **ações do Site** menu no SharePoint, escolha **configurações do Site**.

    2. Em **ações do Site**, escolha o **gerenciar recursos do site** link.

    3. Ao lado de **IntelliTraceTest Feature1**, escolha o **desativar** botão.

    4. Na página de aviso, escolha o **desativar esse recurso** link.

     O manipulador de eventos FeatureDeactivating() gera um erro.

## <a name="BKMK_CollectDiagnosticData">Coletar dados do IntelliTrace usando o Microsoft Monitoring Agent</a>

Se você instalar o agente de monitoramento da Microsoft no sistema que está executando o SharePoint, você pode depurar soluções do SharePoint usando dados que são mais específicos que as informações genéricas IntelliTrace retorna. O agente funciona fora do Visual Studio usando cmdlets do PowerShell para capturar informações de depuração durante a execução de solução do SharePoint.

> [!NOTE]
> As informações de configuração nesta seção são específicas para este exemplo. Para obter mais informações sobre outras opções de configuração, consulte [usando o coletor autônomo do IntelliTrace](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

1. No computador que está executando o SharePoint, [configurar o agente de monitoramento da Microsoft e começar a monitorar sua solução](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector).

2. Desative o recurso:

    1. Sobre o **ações do Site** menu no SharePoint, escolha **configurações do Site**.

    2. Em **ações do Site**, escolha o **gerenciar recursos do site** link.

    3. Ao lado de **IntelliTraceTest Feature1**, escolha o **desativar** botão.

    4. Na página de aviso, escolha o **desativar esse recurso** link.

     Ocorrerá um erro (nesse caso, devido ao erro gerado no manipulador de eventos FeatureDeactivating()).

3. Na janela do PowerShell, execute o [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) comando para criar o arquivo. itrace, interromper o monitoramento e reiniciar a solução do SharePoint.

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="BKMK_DebugSolution">Depurar e corrigir a solução do SharePoint</a>

Agora você pode exibir o arquivo de log do IntelliTrace no Visual Studio para localizar e corrigir o erro na solução do SharePoint.

1. Na pasta \IntelliTraceLogs, abra o arquivo. itrace no Visual Studio.

     O **resumo do IntelliTrace** página será exibida. Como o erro não foi tratado, uma ID de correlação do SharePoint (uma GUID) aparece na área de exceção sem tratamento do **Analysis** seção. Escolha o **pilha de chamadas** botão se você deseja exibir a pilha de chamadas em que ocorreu o erro.

2. Escolha o **depurar exceção** botão.

     Se solicitado, carrega arquivos de símbolo. No **IntelliTrace** janela, a exceção é realçada como "Thrown: erro grave!".

     Na janela do IntelliTrace, escolha a exceção para exibir o código de falha.

3. Corrija o erro abrindo a solução do SharePoint e, em seguida, comentar ou remover o **gerar** instrução na parte superior do procedimento FeatureDeactivating().

4. Recompile a solução no Visual Studio e, em seguida, reimplantá-lo no SharePoint.

5. Desative o recurso executando as seguintes etapas:

    1. Sobre o **ações do Site** menu no SharePoint, escolha **configurações do Site**.

    2. Em **ações do Site**, escolha o **gerenciar recursos do site** link.

    3. Ao lado de **IntelliTraceTest Feature1**, escolha o **desativar** botão.

    4. Na página de aviso, escolha o **desativar esse recurso** link.

6. Abra a lista de tarefas e verifique o **Status** valor da tarefa desativar é "concluído" e seu **% concluída** valor é 100%.

     O código agora é executado corretamente.

## <a name="see-also"></a>Consulte também

[Verificando e depurando o código do SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[Passo a passo: Verifique se o código do SharePoint usando testes de unidade](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
