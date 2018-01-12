---
title: "Implantando, publicando e atualizando pacotes de solução do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5990ab0f6ff6ec02131921f54197dd28e7f4e6ff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="deploying-publishing-and-upgrading-sharepoint-solution-packages"></a>Implantando, publicando e atualizando pacotes de soluções do SharePoint
  Depois de desenvolver uma solução do SharePoint no Visual Studio, você pode implantar seu arquivo de pacote (. wsp) em um servidor SharePoint local ou publicá-lo em um servidor SharePoint local ou remoto. Se você implantar os arquivos, você pode personalizar como os arquivos de pacote (. wsp) são implantados.  
  
> [!NOTE]  
>  Atualmente, apenas as soluções em modo seguro podem ser publicadas em servidores remotos do SharePoint. Para obter mais informações, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploying-publishing-and-upgrading"></a>Implantando, publicando e atualizando  
 *Implantando* refere-se a cópia de um arquivo de solução do SharePoint criado a partir de um projeto do SharePoint no Visual Studio para um host local. Em uma solução de implantação, você pode configurar as etapas de implantação, como Reciclando o pool de serviços de informações da Internet (IIS), ativar a solução após a implantação e assim por diante. Para implantar, usar o **implantar** comando o **criar** menu. Para obter mais informações, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [como: implantar e publicar uma solução do SharePoint a um Site do SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publicando* se refere a carregar um arquivo de solução do SharePoint em modo seguro em um SharePoint remoto site; isto é, um site localizado em outro sistema. Você também pode publicar um arquivo de solução em modo seguro do SharePoint para um local do SharePoint, mas independentemente se o site publicado é local ou remoto, você não pode configurar suas etapas de implantação.  
  
 *Atualizando* refere-se para atualizar uma existente remotamente ou localmente publicada solução do SharePoint. Depois que as alterações são feitas para a solução do SharePoint no Visual Studio, altere o nome de arquivo do pacote da solução, republicar a solução e, em seguida, atualizar a solução após ela republica com êxito. Se você republicar uma solução localmente publicada, você pode substituir o arquivo de solução existente.  
  
## <a name="deploying-packages"></a>Implantando pacotes  
 Você pode implantar os arquivos de pacote para o servidor do SharePoint no computador de desenvolvimento para teste e depuração. Você também pode criar um arquivo de pacote que você pode instalar em outro computador, escolhendo o **publicar no sistema de arquivos** botão de opção de **publicar** caixa de diálogo. O pacote é criado e copiado para o caminho de arquivo local especificado. Para implantar uma solução do SharePoint para o servidor local, use o **implantar** comando o **criar** menu. Para obter mais informações, consulte [como: implantar e publicar uma solução do SharePoint a um Site do SharePoint Local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Para saber como implantar uma definição de lista, adicionar um receptor de evento e use o Designer de pacote e o Designer de recursos, consulte [passo a passo: Implantando uma definição de lista de tarefas de projeto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customizing-the-deployment-process"></a>Personalizando o processo de implantação  
 A tabela a seguir mostra as duas configurações de implantação que você pode usar ao depurar e implantar uma solução do SharePoint.  
  
|Configuração de implantação|Descrição|  
|------------------------------|-----------------|  
|Padrão|A configuração de implantação padrão. As seguintes etapas de implantação são executadas:<br /><br /> 1.  Execute o comando de pré-implantação.<br />2.  Recicle o pool de aplicativos do IIS.<br />3.  Cancele a solução.<br />4.  Adicione solução.<br />5.  Ative recursos.<br />6.  Execute o comando de pós-implantação.<br /><br /> Quando um pacote é desinstalado, as etapas a seguir retração são executadas.<br /><br /> 1.  Recicle o pool de aplicativos do IIS.<br />2.  Cancele a solução.|  
|Nenhuma ativação|Essa configuração de implantação é executado as mesmas etapas, como a configuração padrão, mas ignora a etapa de ativação.|  
  
 Você pode criar suas próprias configurações de implantação para concluir uma única etapa ou alterar a ordem das etapas no processo de implantação. Para obter mais informações, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 Você também pode adicionar comandos a serem executados antes e após a implantação. Para obter mais informações, consulte [como: definir comandos de implantação do SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publishing-packages-to-a-remote-or-local-server"></a>Publicar pacotes em um servidor Local ou remoto  
 Para publicar uma solução do SharePoint em modo seguro em um servidor remoto, na barra de menus, escolha **criar**, **publicar**e, em seguida, no **publicar** caixa de diálogo caixa, escolha o **Publicar no Site do SharePoint** botão de opção, fornecendo a URL do servidor remoto, como **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 Para publicar uma solução do SharePoint para um servidor local, no **publicar** caixa de diálogo caixa, escolha o **publicar no sistema de arquivos** botão de opção, fornecendo um caminho de sistema local.  
  
 Depois de uma solução com êxito publica no SharePoint, a solução aparece no **Galeria de soluções** onde você pode ativá-la. Para obter mais informações, consulte [como: implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrading-published-packages"></a>Atualizando pacotes publicados  
 Se você fizer alterações em um projeto do SharePoint no Visual Studio depois que ele é publicado, o pacote publicado deve ser atualizado para incluir as alterações. Para atualizar com êxito, um pacote deve ter um nome exclusivo. Se um pacote com o mesmo nome for encontrado no site do SharePoint - que pode ocorrer quando você estiver atualizando um aplicativo existente - os alertas de um erro se o nome do arquivo estão em conflito e permite que você renomeie o pacote. Depois de republicação, o novo pacote é exibido no site do SharePoint e pode ser atualizado. Um pacote atualizado atualiza a solução usando os dados do pacote mais antigo e ativa a solução no SharePoint. Para obter mais informações, consulte [como: implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  