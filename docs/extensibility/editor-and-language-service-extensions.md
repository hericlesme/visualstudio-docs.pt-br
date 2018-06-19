---
title: Editor e linguagem de extensões de serviço | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2fceb0487c23dc34d3f4f4937d7a5998340ae3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126623"
---
# <a name="editor-and-language-service-extensions"></a>Editor e extensões de serviço de linguagem
Você pode estender a maioria dos recursos do editor de código do Visual Studio. O editor é baseado no Windows Presentation Foundation (WPF) e é gravado em código gerenciado. Embora esse design difere designs em versões anteriores do Visual Studio, ele fornece a maioria dos mesmos recursos. Para estender o editor, use o Managed Extensibility Framework (MEF).  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram desenvolvidos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso de modelos de item do Editor.|  
|[Estender o editor e os serviços de linguagem](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que apresentam o design e os recursos do editor do núcleo e mostram como estendê-lo.|  
|[Interfaces herdadas no Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links para documentos que explicam como acessar o editor de núcleo de código existente.|  
|[Criar designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|  
|[Extensibilidade do serviço de linguagem herdado](../extensibility/internals/legacy-language-service-extensibility.md)|Links para documentos que descrevem como integrar linguagens de programação em Visual Studio.|  
|[MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)|Apresenta o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Apresenta o Windows Presentation Foundation (WPF).|