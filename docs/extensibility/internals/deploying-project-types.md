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
ms.openlocfilehash: e7673839e44e913d7d0a219400142fe7e6a0b95e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instala um novo agregador do tipo de projeto (ProjectAggregator2.dll) e também um pacote do Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona alternativas limitações de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregador que impedem a tipos de projeto de código gerenciado funcionando corretamente. As etapas a seguir descrevem como alterar seu VSPackage para usar o novo agregador.  
  
1.  Remova o projeto NativeHierarchyWrapper de sua solução.  
  
2.  Remova todos os binários NativeHierarchyWrapper da sua instalação.  
  
3.  Adicione ProjectAggregator2.msi à sua instalação.