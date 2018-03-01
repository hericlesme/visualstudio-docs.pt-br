---
title: "Migrando soluções do Office para o .NET Framework 4 ou posterior | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 8cb61186c7e8260578e9b69242c594c198f7e525
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migrando soluções do Office para o .NET Framework 4 ou posterior
  Se a estrutura de destino de um projeto do Office será alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, algumas etapas adicionais podem ser necessários para continuar a executar a solução no desenvolvimento e o usuário final computadores. Para obter mais informações, consulte [alterações necessárias para executar projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Além disso, o projeto não pode compilar. Alguns recursos de projetos do Office têm modelos de programação diferentes para diferentes versões do .NET Framework. Quando a estrutura de destino de um projeto do Office é alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, você deve fazer as seguintes alterações de código ao projeto:  
  
-   [Atualizando projetos do Excel e Word que você migrar para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Atualizando personalizações da faixa de opções em projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Atualizando as regiões de formulário em projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 A estrutura de destino de um projeto do Office muda quando você atualizar o projeto de uma versão anterior do Visual Studio. Para obter mais informações, consulte [atualizando e Migrando soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Para obter mais informações sobre por que alguns recursos em projetos do Office têm um modelo de programação diferente quando você direcionar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, consulte [muda para o Design de projetos do Office destinados ao .NET Framework 4 ou o .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Como direcionar para uma versão do .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Solucionando problemas de erros em soluções do Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Suporte adicional para erros em Soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  