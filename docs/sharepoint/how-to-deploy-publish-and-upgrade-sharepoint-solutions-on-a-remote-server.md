---
title: "Como: implantar, publicar e atualizar soluções do SharePoint em um servidor remoto | Microsoft Docs"
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
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 519f40017fff5dd3241f4563c5a85d0d0d15c01b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Como implantar, publicar uma atualizar soluções do SharePoint em um servidor remoto
  Além de implantar soluções do SharePoint para o sistema local, você pode publicar soluções em modo seguro do SharePoint para locais remotos ou sites locais do SharePoint. O processo de publicação remoto copia o arquivo. wsp no servidor do SharePoint, instala a solução e, em seguida, permite que você ative a solução. Você também pode atualizar uma instalação remota de solução do SharePoint depois que forem feitas alterações a ele.  
  
## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Para publicar uma solução do SharePoint em modo seguro em um servidor remoto do SharePoint  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o projeto em modo seguro do SharePoint que você deseja publicar e, em seguida, escolha **publicar**.  
  
2.  No **publicar** caixa de diálogo caixa, escolha o **publicar no Site do SharePoint** botão de opção e, em seguida, digite uma URL para um site de publicação online, como o exemplo a seguir: **https:// mytestsite.SharePoint.microsoftonline.com**.  
  
3.  Escolha o **abrir a página da Galeria de soluções no navegador após a publicação** botão de opção para exibir a lista de soluções de **Galeria de soluções** página após a publicação.  
  
4.  Escolha o **publicar** botão.  
  
5.  Faça logon no servidor remoto se a autenticação do usuário é necessária.  
  
     O progresso da publicação é exibido no Visual Studio **saída** janela. Quando o processo for concluído, o arquivo de solução (. wsp) é instalado no servidor do SharePoint remoto. No entanto, ele ainda deve ser ativado antes de ser usada no SharePoint.  
  
6.  Sobre o **Galeria de soluções** página, selecione o aplicativo do SharePoint e, em seguida, na faixa de opções, escolha o **ativar** botão.  
  
7.  No **ativar solução** caixa de diálogo, na faixa de opções, escolha o **ativar** novamente.  
  
     O **Status** coluna o **Galeria de soluções** página indica que o aplicativo está ativo.  
  
## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Para atualizar uma solução do SharePoint em modo seguro em um servidor remoto do SharePoint  
 Se uma solução em modo seguro do SharePoint já estiver publicada em um servidor remoto, o processo a seguir permite que você atualizá-lo depois de fazer alterações para o aplicativo no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Renomeie o pacote do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para fazer isso, em **Solution Explorer** abrir o pacote. Ele aparece no **Explorador de pacotes**.  
  
2.  Em **Explorador de pacotes**, além de **nome** , altere o nome do pacote para um nome exclusivo.  
  
3.  Salvar o projeto.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o projeto e, em seguida, escolha **publicar**.  
  
5.  No **publicar** caixa de diálogo caixa, escolha o **publicar no Site do SharePoint** botão de opção e, em seguida, se a URL para o servidor remoto em que a solução foi salvo estiver ausente, insira-a.  
  
6.  Escolha o **abrir a página da Galeria de soluções no navegador após a publicação** botão de opção para exibir a lista de soluções de **Galeria de soluções** página após a publicação.  
  
7.  Escolha o **publicar** botão.  
  
8.  Faça logon no servidor remoto se a autenticação do usuário é necessária.  
  
     Se conectado ao servidor remoto recentemente, a autenticação não pode ser necessária.  
  
     Se a versão mais antiga do aplicativo que tem o mesmo nome ainda existe no servidor do SharePoint, você obterá um erro que um pacote com o mesmo nome já existe no servidor do SharePoint. Você deve renomear o pacote para um nome exclusivo antes da publicação.  
  
9. Escolha o novo aplicativo no SharePoint e, em seguida, na faixa de opções, escolha o **atualização** botão.  
  
10. No **atualizar solução** caixa de diálogo, na faixa de opções, escolha o **atualização** novamente. O **Status** coluna o **Galeria de soluções** página agora deve indicar que o aplicativo está ativo.  
  
     A versão antiga da solução está desativada, a nova versão da solução é atualizada com dados mantidos da solução antiga e nova solução é ativada no SharePoint.  
  
## <a name="see-also"></a>Consulte também  
 [Como: implantar e publicar uma solução do SharePoint para um local do SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Criando pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Como adicionar e remover funcionalidades e itens de um pacote usando o Package Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  