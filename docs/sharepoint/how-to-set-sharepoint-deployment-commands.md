---
title: "Como: definir comandos de implantação do SharePoint | Microsoft Docs"
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
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c67972dddedcd05338d793883b2dcba0789d48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Como definir comando de implantação do SharePoint
  Você pode personalizar o processo de implantação, definindo comandos pré e pós-implantação. Esses comandos são executados antes e depois de outras ações de implantação quando você depura soluções do SharePoint no Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Para adicionar um comando de pré-implantação  
  
1.  Na barra de menus, escolha **projeto**, *ProjectName***propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **linha de comando de pré-implantação** texto, digite os comandos do MS-DOS ou MSBuild para personalizar esta etapa.  
  
     Por exemplo, para listar o conteúdo do diretório antes da conclusão da implantação, digite **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Para adicionar um comando de pós-implantação  
  
1.  Na barra de menus, escolha **projeto**, *ProjectName***propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **linha de comando de pós-implantação** texto, digite os comandos do MS-DOS ou MSBuild para personalizar esta etapa.  
  
     Por exemplo, para listar o conteúdo do diretório após a conclusão da implantação, digite **dir**. Para usar uma variável de MSBuild para copiar o assembly do diretório de compilação, digite **copiar TargetPath c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  