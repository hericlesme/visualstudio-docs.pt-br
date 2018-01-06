---
title: "Tipos de projeto de implantação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2171a940951d828df358d09dae5fec68b6475e4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instala um novo agregador do tipo de projeto (ProjectAggregator2.dll) e também um pacote do Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona alternativas limitações de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregador que impedem a tipos de projeto de código gerenciado funcionando corretamente. As etapas a seguir descrevem como alterar seu VSPackage para usar o novo agregador.  
  
1.  Remova o projeto NativeHierarchyWrapper de sua solução.  
  
2.  Remova todos os binários NativeHierarchyWrapper da sua instalação.  
  
3.  Adicione ProjectAggregator2.msi à sua instalação.