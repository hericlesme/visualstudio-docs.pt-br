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
ms.openlocfilehash: 3406e65ad96b93cd21890d61270c0ed989ad496c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756565"
---
# <a name="how-to-add-a-resource-file"></a>Como: adicionar um arquivo de recurso
  Os comandos para adicionar arquivos de recurso é no menu de atalho do nó da solução e nós de recurso no Gerenciador de soluções. Para obter mais informações, consulte [soluções do SharePoint Localizando](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Para adicionar um arquivo de recurso global para uma solução do SharePoint  
  
1.  No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra uma solução do SharePoint.  
  
2.  Na **Gerenciador de soluções**, escolha um nó de projeto do SharePoint e, em seguida, na barra de menus, escolha **Project** > **Add New Item**.  
  
3.  No **Adicionar Novo Item** diálogo caixa, escolha o **arquivo de recursos globais** modelo e, em seguida, escolha o **adicionar** botão.  
  
    > [!NOTE]  
    >  O modelo de item de projeto do arquivo de recursos globais só aparece quando um item de projeto do SharePoint é selecionado.  
  
4.  No **adicionar recurso** caixa de diálogo, escolha uma cultura para o arquivo de recurso, como o inglês (Estados Unidos).  
  
     Esta etapa adiciona um arquivo de recurso global à sua solução no formato, recurso * x ***.*** cultura ***.** resx, tais como, *Resource1.en resx*.  
  
5.  Quando o **Editor de recursos** é aberto no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], adicionar recursos ao arquivo de recurso.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Para adicionar um arquivo de recurso a um recurso do SharePoint  
  
1.  Se a solução do SharePoint não ainda estiver aberta no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra a solução.  
  
2.  Na **Gerenciador de soluções**, abra o menu de atalho para o nome de um recurso sob a **recursos** nó e, em seguida, escolha **adicionar recurso**.  
  
     Esta etapa adiciona um arquivo de recurso para o recurso no formato * ResourceFileName ***.*** cultura ***.** resx, tais como, *Feature1.en resx*.  
  
3.  Quando o **Editor de recursos** é aberto no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], adicionar recursos ao arquivo de recurso.  
  
## <a name="see-also"></a>Consulte também
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
