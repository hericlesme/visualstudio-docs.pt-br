---
title: 'Como: definir comandos de implantação do SharePoint | Microsoft Docs'
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
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8779ba4ee4cf9803982d9849b3af7c83930d8a5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Como definir comando de implantação do SharePoint
  Você pode personalizar o processo de implantação, definindo comandos pré e pós-implantação. Esses comandos são executados antes e depois de outras ações de implantação quando você depura soluções do SharePoint no Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Para adicionar um comando de pré-implantação  
  
1.  Na barra de menus, escolha **projeto**, * * ProjectName**propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **linha de comando de pré-implantação** texto, digite os comandos do MS-DOS ou MSBuild para personalizar esta etapa.  
  
     Por exemplo, para listar o conteúdo do diretório antes da conclusão da implantação, digite **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Para adicionar um comando de pós-implantação  
  
1.  Na barra de menus, escolha **projeto**, * * ProjectName**propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **linha de comando de pós-implantação** texto, digite os comandos do MS-DOS ou MSBuild para personalizar esta etapa.  
  
     Por exemplo, para listar o conteúdo do diretório após a conclusão da implantação, digite **dir**. Para usar uma variável de MSBuild para copiar o assembly do diretório de compilação, digite **copiar TargetPath c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  