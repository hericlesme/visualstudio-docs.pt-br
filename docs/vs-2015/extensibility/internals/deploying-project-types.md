---
title: Implantar tipos de projeto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66069ac71fbe59e8b63126d66d2a0cc63ed095bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464868"
---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tipos de projeto de implantação](https://docs.microsoft.com/visualstudio/extensibility/internals/deploying-project-types).  
  
[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instala um novo agregador do tipo de projeto (ProjectAggregator2.dll) e também um pacote do Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona alternativas limitações no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeto agregador que impedem a tipos de projeto de código gerenciado de funcionar corretamente. As etapas a seguir descrevem como alterar o VSPackage para usar o novo agregador.  
  
1.  Remova o projeto de NativeHierarchyWrapper da sua solução.  
  
2.  Remova os binários do NativeHierarchyWrapper de sua configuração.  
  
3.  Adicione ProjectAggregator2.msi à sua instalação.

