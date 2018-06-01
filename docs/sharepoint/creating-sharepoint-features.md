---
title: Criar recursos do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d119e84bba07c68e8d0466902d52d4ed9d151123
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692009"
---
# <a name="creating-sharepoint-features"></a>Criar recursos do SharePoint
  Você pode usar um recurso do SharePoint para agrupar itens de projeto do SharePoint relacionados para facilitar a implantação. Você pode criar recursos, definir escopos e marcar outros recursos como dependências usando o Designer de recursos do SharePoint. O designer também gera um manifesto, que é um arquivo XML que descreve cada recurso.  
  
## <a name="add-features-to-the-sharepoint-solution"></a>Adicionar recursos para a solução do SharePoint
 Você pode adicionar um recurso para a solução do SharePoint usando o Gerenciador de soluções ou o Gerenciador de pacotes. Você pode usar um dos métodos a seguir para adicionar um recurso.  
  
-   Em **Solution Explorer**, abra o menu de atalho para **recursos**e, em seguida, escolha **adicionar recurso**.  
  
-   Em **Packaging Explorer**, abra o menu de atalho para o pacote e, em seguida, escolha **adicionar recurso**.  
  
## <a name="using-the-feature-designer"></a>Usando o designer de recursos
 Uma solução do SharePoint pode conter um ou mais recursos do SharePoint, que são agrupadas sob o nó de recurso no Gerenciador de soluções. Cada recurso tem seu próprio **recurso Designer** que você pode usar para personalizar as propriedades do recurso. Para obter mais informações, consulte [como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md). Para diferenciar recursos uns dos outros, você pode configurar as propriedades do recurso, como o título, descrição, versão e escopo.  
  
### <a name="feature-designer-options"></a>Opções do designers de recursos
 Depois de criar um recurso, você pode usar o Designer de recursos para personalizá-lo.  
  
 A tabela a seguir descreve as propriedades do recurso que são exibidas no Designer de recursos.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|Título|Opcional. O título padrão do recurso é definido como *SolutionName* *FeatureName*.|  
|Descrição|Opcional. A descrição do recurso do SharePoint.|  
|Escopo|Necessário. Se um recurso for criado usando **Solution Explorer**, o escopo é definido na Web por padrão.<br /><br /> -Farm: Ative um recurso para um farm de servidores inteiro.<br /><br /> -Site: Ative um recurso para todos os sites em uma coleção de sites.<br /><br /> -Web: Ative um recurso para um site específico.<br /><br /> -WebApplication: Ative um recurso para todos os sites da web em um aplicativo web.|  
|Itens da solução|Todos os itens do SharePoint que pode ser adicionado ao recurso.|  
|Itens no recurso|Os itens de projeto do SharePoint que foram adicionados para o recurso.|  
  
## <a name="add-and-remove-sharepoint-project-items"></a>Adicionar e remover itens de projeto do SharePoint
 Você pode selecionar quais itens de projeto do SharePoint que você deseja adicionar um recurso do SharePoint para implantação. Use o **recurso Designer** para adicionar e remover itens de recursos e exibir o manifesto do recurso. Para obter mais informações, consulte [como: adicionar e remover itens de recursos do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).  
  
## <a name="add-feature-dependencies"></a>Adicionar dependências de recurso
 Você pode configurar o manifesto do recurso para que o servidor do SharePoint ativa certos recursos antes que o recurso está ativado. Por exemplo, se o recurso do SharePoint depende de outros recursos de funcionalidade ou dados, o servidor do SharePoint pode primeiro tente ativar os recursos que o recurso depende. Para obter mais informações, consulte [como: adicionar e remover dependências de recurso](../sharepoint/how-to-add-and-remove-feature-dependencies.md).  
  
## <a name="see-also"></a>Consulte também
 [Como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Como: adicionar e remover itens de recursos do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [Como adicionar e remover dependências de recurso](../sharepoint/how-to-add-and-remove-feature-dependencies.md)  
  
  
