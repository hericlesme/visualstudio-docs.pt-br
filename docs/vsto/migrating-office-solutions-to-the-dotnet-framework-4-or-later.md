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
ms.openlocfilehash: 830dcdb9e42472aa712c86ddb117b3b8003ac4d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  