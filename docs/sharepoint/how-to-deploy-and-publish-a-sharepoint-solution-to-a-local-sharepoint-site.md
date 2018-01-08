---
title: "Como: implantar e publicar uma solução do SharePoint para um local do SharePoint | Microsoft Docs"
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
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9e643eb31062bcd81302fba6e7d35cc8dfa674b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Como: implantar um e publicar uma solução do SharePoint em um local do SharePoint
  Você pode implantar ou publicar soluções do SharePoint em um servidor local do SharePoint no computador de desenvolvimento. O processo de implantação copia o arquivo. wsp no servidor do SharePoint, instala a solução e, em seguida, ativa os recursos. O processo de publicação só copia o arquivo. wsp no servidor do SharePoint e instala-o. Você deve ativar manualmente para habilitá-lo no SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implantar uma solução do SharePoint para o servidor local do SharePoint  
  
1.  Em **Solution Explorer**, escolha o projeto que você deseja implantar.  
  
2.  Na barra de menus, escolha **criar**, **implantar solução**.  
  
     O arquivo. wsp é criado e instalado no servidor do SharePoint local. Além disso, os recursos são ativados.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar uma solução do SharePoint em um servidor local do SharePoint  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o projeto do SharePoint que você deseja publicar e, em seguida, escolha **publicar**.  
  
2.  No **publicar** caixa de diálogo caixa, escolha o **publicar no sistema de arquivos** botão de opção.  
  
3.  No **local de destino** caixa de texto, digite um caminho local e, em seguida, escolha o **publicar** botão.  
  
     O progresso da publicação é exibido no Visual Studio **saída** janela. Quando o processo for concluído, o arquivo de solução (. wsp) é instalado no servidor do SharePoint local. No entanto, ele ainda deve ser ativado para ser usado no SharePoint. Se o arquivo de solução já existir, um erro ocorre e perguntando se deseja substituir o arquivo existente. Para obter informações sobre como atualizar o pacote, consulte a seção sobre como atualizar pacotes remotos em [como: implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Criando pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Como adicionar e remover funcionalidades e itens de um pacote usando o Package Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  