---
title: Atualizando itens de projeto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: 10005b38f01c3cad97cf8c7aab391e4546737295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474203"
---
# <a name="upgrading-project-items"></a>Atualizando itens de projeto
Se você adicionar ou gerenciar itens de sistemas de projeto, você não implemente, você talvez precise participar do processo de atualização do projeto. Crystal Reports é um exemplo de um item que pode ser adicionado ao sistema de projeto.  
  
 Normalmente, os implementadores de item de projeto desejam aproveitar um projeto já totalmente instanciado e atualizado porque eles precisam saber o que o projeto são referências e o que outras propriedades do projeto existem para tomar uma decisão de atualização.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Para obter a notificação de atualização de projeto  
  
1.  Defina o <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> sinalizador (definida em vsshell80.idl) em sua implementação de item de projeto. Isso faz com que o item de projeto VSPackage automaticamente carregar quando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell determina que um sistema de projeto está no processo de atualização.  
  
2.  Aconselhamos a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> por meio da interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3.  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é disparado após a implementação do sistema de projeto tiver concluído suas operações de atualização e o novo projeto atualizado. Dependendo do cenário, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é disparado após o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> métodos.  
  
### <a name="to-upgrade-the-project-item-files"></a>Para atualizar os arquivos de item de projeto  
  
1.  Você deve gerenciar cuidadosamente o processo de backup do arquivo em sua implementação de item de projeto. Isso se aplica especificamente para um backup de lado a lado, em que o `fUpgradeFlag` parâmetro do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método está definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, onde os arquivos que tinham sido feitos são posicionados ao longo de arquivos lado que são designados como ". old". Arquivos de backup mais antigos do que a hora do sistema quando o projeto foi atualizado podem ser designados como obsoletos. Além disso, eles poderão ser substituídos, a menos que você siga etapas específicas para evitar isso.  
  
2.  No momento em seu item de projeto recebe uma notificação de atualização de projeto, o **Assistente de conversão do Visual Studio** ainda é exibido. Portanto, você deve usar os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface para fornecer mensagens de atualização para o Assistente de interface do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Assistente de conversão do Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Atualizando projetos personalizados](../misc/upgrading-custom-projects.md)