---
title: Migrando soluções do Office para o .NET Framework 4 ou posterior | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac244bebb1a625c7858a62399ee79126e309cf2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571793"
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migrando soluções do Office para o .NET Framework 4 ou posterior
  Se a estrutura de destino de um projeto do Office será alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, algumas etapas adicionais podem ser necessários para continuar a executar a solução no desenvolvimento e o usuário final computadores. Para obter mais informações, consulte [exigiu alterações para executar projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Além disso, o projeto não pode compilar. Alguns recursos de projetos do Office têm modelos de programação diferentes para diferentes versões do .NET Framework. Quando a estrutura de destino de um projeto do Office é alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior de uma versão anterior do .NET Framework, você deve fazer as seguintes alterações de código ao projeto:  
  
-   [Atualizar projetos do Excel e Word migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Atualizar personalizações da faixa de opções em projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Atualizar regiões do formulário em projetos do Office migrados para o .NET Framework 4 ou o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 A estrutura de destino de um projeto do Office muda quando você atualizar o projeto de uma versão anterior do Visual Studio. Para obter mais informações, consulte [atualizar e migrar soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Para obter mais informações sobre por que alguns recursos em projetos do Office têm um modelo de programação diferente quando você direcionar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, consulte [muda para o design dos projetos do Office destinados ao .NET Framework 4 ou o .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Visual Studio Tools para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Como: uma versão do .NET Framework de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Solucionar problemas de erros em soluções do Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Suporte adicional para erros em soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  