---
title: Tipos de projeto de implantação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala um novo agregador do tipo de projeto (ProjectAggregator2.dll) e também um pacote do Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona alternativas limitações de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregador que impedem a tipos de projeto de código gerenciado funcionando corretamente. As etapas a seguir descrevem como alterar seu VSPackage para usar o novo agregador.  
  
1.  Remova o projeto NativeHierarchyWrapper de sua solução.  
  
2.  Remova todos os binários NativeHierarchyWrapper da sua instalação.  
  
3.  Adicione ProjectAggregator2.msi à sua instalação.