---
title: Criando um controle de origem plug-in | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04c6125004aaf2740b54acdce91bef032647c6e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-source-control-plug-in"></a>Criando um controle de origem plug-in
O SDK do Visual Studio fornece recursos que permitem que você adicionar o recurso de controle de origem para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Ele permite usar qualquer DLL de plug-in que esteja em conformidade com a API de plug-in de controle de origem descritos nesta documentação.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Descreve como instalar um plug-in de controle de origem e destaca as versões de API de plug-in de controle do código-fonte disponíveis no momento.  
  
 [Arquitetura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Usa um diagrama de arquitetura para explicar a integração de controle de origem plug-in com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Fornece orientação sobre como testar a instalação e operação de um plug-in de controle de origem.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um controle de origem VSPackage que não só fornece a funcionalidade de controle de origem, mas substitui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem.  
  
 [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos da API de plug-in de controle de origem.  
  
 [Controle do código-fonte](../../extensibility/internals/source-control.md)  
 Discute as opções para implementar o controle de origem como um recurso integrado do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].