---
title: Elementos de Design de VSPackage de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 234346aba360d70d3bbc673067d2634a5112d0f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-design-elements"></a>Elementos de Design de VSPackage de controle do código-fonte
Os tópicos nesta seção descrevem a estrutura de controle de origem de VSPackage deve implementar para integração profunda. Também lista as interfaces e serviços que a fonte de controle VSPackage podem implementar e os serviços e interfaces o VSPackage do controle de origem pode usar outros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes para dar suporte a sua fonte de modelo e a funcionalidade de controle.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Define a estrutura do controle de origem VSPackage.  
  
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Lista de serviços e interfaces relacionadas a pacotes de controle de origem.  
  
 [Serviços fornecidos](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descreve o serviço de controle de origem fornecido pelo controle de origem VSPackage.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um controle de origem VSPackage que não só fornece a funcionalidade de controle de origem, mas pode ser usado para personalizar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem.