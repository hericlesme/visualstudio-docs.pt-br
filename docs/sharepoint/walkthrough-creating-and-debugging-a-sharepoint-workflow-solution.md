---
title: "Passo a passo: Criando e depurando uma solução de fluxo de trabalho do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 687116b1fc7f3ad935583b41ff9c19d2d5d13613
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>Instruções passo a passo: criando e depurando uma solução de fluxo de trabalho do SharePoint
  Este passo a passo demonstra como criar um modelo de fluxo de trabalho sequencial básico. O fluxo de trabalho verifica uma propriedade de uma biblioteca de documentos compartilhados para determinar se um documento foi revisado. Se o documento foi revisado, o fluxo de trabalho for concluída.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Criando um projeto de fluxo de trabalho sequencial do SharePoint lista definição no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Criando atividades de fluxo de trabalho.  
  
-   Manipulação de eventos de atividade de fluxo de trabalho.  
  
> [!NOTE]  
>  Embora este passo a passo usa um projeto de fluxo de trabalho sequencial, o processo é idêntico para um projeto de fluxo de trabalho de máquina de estado.  
>   
>  Além disso, seu computador pode mostrar diferentes nomes ou locais para alguns de usuário do Visual Studio elementos de interface nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Microsoft Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>Adicionando propriedades para o SharePoint compartilhado a biblioteca de documentos  
 Para acompanhar o status de revisão de documentos de **documentos compartilhados** biblioteca, vamos criar três novas propriedades para documentos compartilhados no nosso site do SharePoint: `Status`, `Assignee`, e `Review Comments`. Podemos definir essas propriedades no **documentos compartilhados** biblioteca.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Para adicionar propriedades aos compartilhado do SharePoint para biblioteca de documentos  
  
1.  Abrir um site do SharePoint, como http://\<nome do sistema > / SitePages/Home.aspx em um navegador da Web.  
  
2.  Na barra de início rápido, escolha **SharedDocuments**.  
  
3.  Escolha **biblioteca** no **ferramentas de biblioteca** de faixa de opções e, em seguida, escolha o **criar coluna** botão na faixa de opções para criar uma nova coluna.  
  
4.  Nome da coluna **documento Status**, defina seu tipo como **opção (menu para escolher)**, especifique as três opções a seguir e, em seguida, escolha o **Okey** botão:  
  
    -   **Revisão necessária**  
  
    -   **Análise concluída**  
  
    -   **Alterações solicitadas**  
  
5.  Crie duas ou mais colunas e os **destinatário** e **examinar os comentários**. Defina o tipo de coluna do destinatário como uma única linha de texto e o tipo de coluna de examinar os comentários como várias linhas de texto.  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>Permitindo que documentos sejam editados sem a necessidade de um Check-Out  
 É mais fácil de testar o modelo de fluxo de trabalho quando você pode editar os documentos sem precisar fazer check-out. No próximo procedimento, você deve configurar o site do SharePoint para permitir que.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Para habilitar os documentos sejam editados sem check-out  
  
1.  Na barra de início rápido, escolha o **documentos compartilhados** link.  
  
2.  No **ferramentas de biblioteca** de faixa de opções, escolha o **biblioteca** guia e, em seguida, escolha o **configurações da biblioteca** botão para exibir o **definições de biblioteca de documentos** página.  
  
3.  No **configurações gerais** , escolha o **configurações de controle de versão** link para exibir o **configurações de controle de versão** página.  
  
4.  Verifique a configuração de **exigem documentos para fazer check-out antes que eles podem ser editados** é **não**. Se não estiver, altere-o para **não** e, em seguida, escolha o **Okey** botão.  
  
5.  Feche o navegador.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Criando um projeto de fluxo de trabalho sequencial do SharePoint  
 Um fluxo de trabalho sequencial é um conjunto de etapas que é executado na ordem até que a última atividade seja concluída. Neste procedimento, vamos criar um fluxo de trabalho sequencial que se aplicam a nossa lista de documentos compartilhados. O Assistente de fluxo de trabalho permite que você associe o fluxo de trabalho com a definição do site ou a definição de lista e permite que você determine quando o fluxo de trabalho será iniciado.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Para criar um projeto de fluxo de trabalho sequencial do SharePoint  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na barra de menus, escolha **arquivo**, **novo**, **projeto** para exibir o **novo projeto** caixa de diálogo.  
  
3.  Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
4.  No **modelos** painel, escolha o **projeto do SharePoint 2010** modelo.  
  
5.  No **nome** , digite **MySharePointWorkflow** e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
6.  No **especificar o nível de site e segurança de depuração** página, escolha o **implantar como uma solução de farm** botão de opção e, em seguida, escolha o **concluir** botão para aceitar o site padrão e o nível de confiança.  
  
     Esta etapa define o nível de confiança para a solução como solução de farm, a única opção disponível para projetos de fluxo de trabalho. Para obter mais informações, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Em **Solution Explorer**, escolha o nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
8.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** nó.  
  
9. No **modelos** painel, escolha o **o fluxo de trabalho sequencial (somente solução de Farm)** modelo e, em seguida, escolha o **adicionar** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
10. No **especifique o nome do fluxo de trabalho para depuração** página, aceite o nome padrão (**MySharePointWorkflow - Workflow1**). Mantenha o valor de tipo de modelo de fluxo de trabalho padrão, **fluxo de trabalho de lista**e, em seguida, escolha o **próximo** botão.  
  
11. No **você gostaria que o Visual Studio para associar automaticamente o fluxo de trabalho em uma sessão de depuração?** página, escolha o **próximo** botão aceitar todas as configurações padrão.  
  
     Esta etapa automaticamente associa o fluxo de trabalho com a biblioteca de documentos compartilhados.  
  
12. No **especificam as condições para a inicialização de seu fluxo de trabalho** , deixe as opções padrão selecionadas no **como você deseja que o fluxo de trabalho para iniciar?** seção e escolha o **concluir** botão.  
  
     Esta página permite que você especifique quando o fluxo de trabalho é iniciado. Por padrão, o fluxo de trabalho inicia o quando um usuário inicie manualmente no SharePoint ou quando um item ao qual o fluxo de trabalho está associado é criado.  
  
## <a name="creating-workflow-activities"></a>Criando atividades de fluxo de trabalho  
 Fluxos de trabalho contém um ou mais *atividades* que representam ações a serem executadas. Use o designer de fluxo de trabalho para organizar atividades para um fluxo de trabalho. Neste procedimento, vamos adicionar duas atividades do fluxo de trabalho: HandleExternalEventActivity e OnWorkFlowItemChanged. Essas atividades monitoram o status de revisão de documentos de **documentos compartilhados** lista  
  
#### <a name="to-create-workflow-activities"></a>Para criar atividades de fluxo de trabalho  
  
1.  O fluxo de trabalho deve ser exibido no designer de fluxo de trabalho. Se não for, em seguida, abra o **workflow1** ou **Workflow1.vb** na **Gerenciador de soluções**.  
  
2.  No designer, escolha o **OnWorkflowActivated1** atividade.  
  
3.  No **propriedades** janela, digite **onWorkflowActivated** lado a **Invoked** propriedade e, em seguida, escolha a tecla Enter.  
  
     Abre o Editor de código, e um método de manipulador de eventos chamado onWorkflowActivated é adicionado ao arquivo de código Workflow1.  
  
4.  Volte para o designer de fluxo de trabalho, abra a caixa de ferramentas e, em seguida, expanda o **v 3.0 do fluxo de trabalho do Windows** nó.  
  
5.  No **v 3.0 do fluxo de trabalho do Windows** nó do **caixa de ferramentas**, execute um dos seguintes conjuntos de etapas:  
  
    1.  Abra o menu de atalho para o **enquanto** atividade e, em seguida, escolha **cópia**. No designer de fluxo de trabalho, abra o menu de atalho para a linha abaixo de **onWorkflowActivated1** atividade e, em seguida, escolha **colar**.  
  
    2.  Arraste o **enquanto** atividade do **caixa de ferramentas** para o designer de fluxo de trabalho e conecte-se a atividade para a linha no **onWorkflowActivated1** atividade.  
  
6.  Escolha o **WhileActivity1** atividade.  
  
7.  No **propriedades** janela, defina **condição** a condição de código.  
  
8.  Expanda o **condição** propriedade, digite **isWorkflowPending** ao lado de filho **condição** propriedade e, em seguida, escolha a tecla Enter.  
  
     Abre o Editor de códigos, e um método chamado isWorkflowPending é adicionado ao arquivo de código Workflow1.  
  
9. Volte para o designer de fluxo de trabalho, abra a caixa de ferramentas e, em seguida, expanda o **fluxo de trabalho do SharePoint** nó.  
  
10. No **fluxo de trabalho do SharePoint** nó do **caixa de ferramentas**, execute um dos seguintes conjuntos de etapas:  
  
    -   Abra o menu de atalho para o **OnWorkflowItemChanged** atividade e, em seguida, escolha **cópia**. No designer de fluxo de trabalho, abra o menu de atalho para a linha dentro de **whileActivity1** atividade e, em seguida, escolha **colar**.  
  
    -   Arraste o **OnWorkflowItemChanged** atividade do **caixa de ferramentas** para o designer de fluxo de trabalho e conecte-se a atividade para a linha dentro de **whileActivity1** atividade.  
  
11. Escolha o **onWorkflowItemChanged1** atividade.  
  
12. No **propriedades** janela, defina as propriedades conforme mostrado na tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invocado**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>Manipulação de eventos de atividade  
 Por fim, verifique o status do documento de cada atividade. Se o documento foi revisado, o fluxo de trabalho é concluído.  
  
#### <a name="to-handle-activity-events"></a>Para tratar eventos de atividade  
  
1.  Em workflow1 ou Workflow1.vb, adicione o seguinte campo na parte superior do `Workflow1` classe. Esse campo é usado em uma atividade para determinar se o fluxo de trabalho é concluído.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Adicione o seguinte método à classe `Workflow1`. Este método verifica o valor de `Document Status` propriedade da lista de documentos para determinar se o documento foi revisado. Se o `Document Status` está definida como `Review Complete`, o `checkStatus` método define o `workflowPending` campo **false** para indicar que o fluxo de trabalho está pronto para concluir.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Adicione o seguinte código para o `onWorkflowActivated` e `onWorkflowItemChanged` métodos para chamar o `checkStatus` método. Quando o fluxo de trabalho é iniciado, o `onWorkflowActivated` chamadas de método de `checkStatus` método para determinar se o documento já foi revisado. Se não tiver sido revisado, o fluxo de trabalho continua. Quando o documento é salvo, o `onWorkflowItemChanged` chamadas de método de `checkStatus` método novamente para determinar se o documento foi revisado. Enquanto o `workflowPending` campo é definido como **true**, o fluxo de trabalho continua a ser executado.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Adicione o seguinte código para o `isWorkflowPending` método para verificar o status do `workflowPending` propriedade. Cada vez que o documento é salvo, o **whileActivity1** atividade chama o `isWorkflowPending` método. Este método examina o <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> propriedade o <xref:System.Workflow.Activities.ConditionalEventArgs> objeto para determinar se o **WhileActivity1** atividade deve continuar ou concluir. Se a propriedade é definida como **true**, a atividade continua. Caso contrário, a atividade é concluída e o fluxo de trabalho for concluída.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Salvar o projeto.  
  
## <a name="testing-the-sharepoint-workflow-template"></a>Testar o modelo de fluxo de trabalho do SharePoint  
 Quando você inicia o depurador, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implanta o modelo de fluxo de trabalho no servidor do SharePoint e associa o fluxo de trabalho com o **documentos compartilhados** lista. Para testar o fluxo de trabalho, inicie uma instância do fluxo de trabalho de um documento no **documentos compartilhados** lista.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Para testar o modelo de fluxo de trabalho do SharePoint  
  
1.  Em workflow1 ou Workflow1.vb, defina um ponto de interrupção ao lado de **onWorkflowActivated** método.  
  
2.  Escolha a tecla F5 para compilar e executar a solução.  
  
     O site do SharePoint é exibida.  
  
3.  No painel de navegação no SharePoint, escolha o **documentos compartilhados** link.  
  
4.  No **documentos compartilhados** página, escolha o **documentos** link o **ferramentas de biblioteca** guia e, em seguida, escolha o **carregar documento** botão .  
  
5.  No **carregar documento** caixa de diálogo caixa, escolha o **procurar** botão, escolha qualquer arquivo de documento, escolha o **abrir** botão e, em seguida, escolha o **Okey** botão.  
  
     Isso carrega o documento selecionado para o **documentos compartilhados** Liste e inicia o fluxo de trabalho.  
  
6.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], verifique se que o depurador para no ponto de interrupção ao lado de `onWorkflowActivated` método.  
  
7.  Pressione a tecla F5 para continuar a execução.  
  
8.  Você pode alterar as configurações para o documento aqui, mas deixá-los com os valores padrão por enquanto, escolhendo o **salvar** botão.  
  
     Isso retorna para o **documentos compartilhados** página do site da Web padrão do SharePoint.  
  
9. No **documentos compartilhados** , verifique se que o valor abaixo de **MySharePointWorkflow - Workflow1** coluna é definida como **em andamento**. Isso indica que o fluxo de trabalho está em andamento e que o documento está aguardando a revisão.  
  
10. No **documentos compartilhados** página, escolha o documento, clique na seta que aparece e, em seguida, escolha o **editar propriedades** item de menu.  
  
11. Definir **documento Status** para **revisão completa**e, em seguida, escolha o **salvar** botão.  
  
     Isso retorna para o **documentos compartilhados** página do site da Web padrão do SharePoint.  
  
12. No **documentos compartilhados** , verifique se que o valor abaixo o **Status do documento** coluna é definida como **revisão completa**. Atualizar o **documentos compartilhados** página e verifique o valor abaixo de **MySharePointWorkflow - Workflow1** coluna é definida como **concluído**. Isso indica que fluxo de trabalho for concluído e que o documento foi revisado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como criar modelos de fluxo de trabalho a partir destes tópicos:  
  
-   Para saber mais sobre as atividades de fluxo de trabalho do SharePoint, consulte [atividades de fluxo de trabalho para o SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Para saber mais sobre as atividades do Windows Workflow Foundation, consulte [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Consulte também  
 [Criação de soluções de fluxo de trabalho do SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Projeto do SharePoint e modelos de Item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  