---
title: 'Como: adicionar e remover recursos e itens de um pacote usando o Packaging Explorer | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dafa11c17968eb5468ecd4eff462ff9474ce5131
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Como adicionar e Remover Funcionalidades e itens de um pacote usando o Packaging Explorer
  Para configurar um pacote para implantar recursos e itens do SharePoint, você pode usar o Gerenciador de pacotes. Você pode ajustar os recursos e itens de projeto do SharePoint em seu arquivo. wsp.  
  
 Como alternativa, você pode usar o Designer de empacotamento para exibir e reordenar os recursos para alterar a ordem de ativação. Para obter mais informações, consulte [como: adicionar e remover recursos e itens de um pacote usando o Designer de pacote](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="opening-the-packaging-explorer"></a>Abrir o Gerenciador de pacotes  
 Você pode usar o procedimento a seguir para abrir o Gerenciador de pacotes, se sua solução do Visual Studio tem pelo menos um projeto do SharePoint. Como alternativa, o Packaging Explorer é aberto automaticamente quando você exibir um designer de pacote ou de recurso. Depois de fechar todos os designers de recurso e pacote, o Gerenciador de pacotes também é fechada.  
  
#### <a name="to-open-the-packaging-explorer"></a>Para abrir o Gerenciador de pacotes  
  
1.  Na barra de menus, escolha **exibição**, **outras janelas**, **Packaging Explorer**.  
  
     O **Packaging Explorer** aparece no **caixa de ferramentas**.  
  
## <a name="adding-a-feature-to-a-package"></a>Adicionar um recurso a um pacote  
 Você pode adicionar recursos novos e existentes a um pacote usando o Packaging Explorer.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Para adicionar um recurso do SharePoint  
  
1.  Abra o **Packaging Explorer**, abra o menu de atalho para o projeto e, em seguida, escolha **adicionar recurso**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Para mover um recurso existente do SharePoint  
  
1.  Abra o **Packaging Explorer**e, em seguida, execute uma das seguintes etapas:  
  
    -   Arraste um **recurso** de um projeto para outro projeto.  
  
    -   Abra o menu de atalho para um recurso, escolha **Recortar**, abra o menu de atalho para o projeto ao qual você deseja mover o recurso e, em seguida, escolha **colar**.  
  
    > [!NOTE]  
    >  Use este procedimento se você tiver mais de um projeto do SharePoint em sua solução.  
  
## <a name="validating-a-feature-or-package"></a>Validar um pacote ou recurso  
 Você pode identificar problemas em potencial nos recursos do SharePoint e os pacotes, validando os arquivos. Erros e avisos são exibidos na janela lista de erros e a janela de saída.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Para validar um pacote ou um recurso do SharePoint  
  
1.  Abra o **Packaging Explorer**.  
  
2.  Abrir um menu de atalho para um recurso ou o pacote e, em seguida, escolha **validar**.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  