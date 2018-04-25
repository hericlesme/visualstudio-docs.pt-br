---
title: 'Como: adicionar um arquivo de recurso | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 132a5b5933b1bc96244238570091e522f8af91d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-resource-file"></a>Como adicionar um arquivo de recurso
  Os comandos para adicionar arquivos de recurso é no menu de atalho do nó da solução e nós de recurso no Gerenciador de soluções. Para obter mais informações, consulte [Localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Para adicionar um arquivo de recurso global para uma solução do SharePoint  
  
1.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abrir uma solução do SharePoint.  
  
2.  Em **Solution Explorer**, escolha um nó do projeto do SharePoint e, em seguida, na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
3.  No **Adicionar Novo Item** caixa de diálogo caixa, escolha o **arquivo de recursos globais** modelo e, em seguida, escolha o **adicionar** botão.  
  
    > [!NOTE]  
    >  O modelo de item de projeto do arquivo de recursos globais só aparece quando um item de projeto do SharePoint é selecionado.  
  
4.  No **adicionar recurso** caixa de diálogo caixa, escolha uma cultura para o arquivo de recurso, como o inglês (Estados Unidos).  
  
     Esta etapa adiciona um arquivo de recurso global para sua solução no formato, recurso * x ***.*** cultura ***.** resx, como Resource1.en-us.  
  
5.  Quando o **Editor de recurso** abre no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], adicionar recursos para o arquivo de recurso.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Para adicionar um arquivo de recursos para um recurso do SharePoint  
  
1.  Se a solução do SharePoint não ainda estiver aberta no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra a solução.  
  
2.  Em **Solution Explorer**, abra o menu de atalho para o nome de um recurso sob o **recursos** nó e, em seguida, escolha **adicionar recurso do recurso**.  
  
     Esta etapa adiciona um arquivo de recurso para o recurso no formato, * ResourceFileName ***.*** cultura ***.** resx, como Feature1.en-us.  
  
3.  Quando o **Editor de recurso** abre no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], adicionar recursos para o arquivo de recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  