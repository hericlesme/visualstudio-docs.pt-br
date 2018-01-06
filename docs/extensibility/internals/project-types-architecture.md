---
title: Arquitetura de tipos de projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34402ae0b998d4ae534507e23ffa31e0d7cef9bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="project-types-architecture"></a>Arquitetura de tipos de projeto
Esta seção contém informações detalhadas sobre a arquitetura de tipos de projeto em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)  
 Lista os serviços que pode consumir um tipo de projeto e as interfaces que ele deve implementar.  
  
 [Componentes principais do modelo de projeto](../../extensibility/internals/project-model-core-components.md)  
 Descreve as interfaces de tipos de projeto devem implementar e, opcionalmente, podem ser implementados para fornecer funcionalidade adicional.  
  
 [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)  
 Tipo de ajuda você a decidir quando você deve criar um projeto e quando você pode usar outro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recurso de extensibilidade, como VSPackages e editores para alcançar o mesmo objetivo.  
  
 [Seleção e hierarquias](../../extensibility/internals/hierarchies-and-selection.md)  
 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa hierarquias e o contexto de seleção para fornecer uma experiência de usuário consistente e simplificado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Explica como subtipos de projeto permitem personalizar o comportamento dos sistemas de projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece uma visão geral de projetos como blocos de construção básicos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). São fornecidos links para tópicos adicionais que explicam como projetos de controle de criar e compilar o código.