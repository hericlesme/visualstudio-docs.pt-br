---
title: Extensões de serviço do Editor e linguagem | Microsoft Docs
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
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e464b46185339bd1a22b433e4784154dbdb818c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475318"
---
# <a name="editor-and-language-service-extensions"></a>Editor e extensões do serviço de linguagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Editor e extensões do serviço de linguagem](https://docs.microsoft.com/visualstudio/extensibility/editor-and-language-service-extensions).  
  
Você pode estender a maioria dos recursos do editor de código do Visual Studio. O editor é baseado no Windows Presentation Foundation (WPF) e é escrito em código gerenciado. Embora esse design difere os designs em versões anteriores do Visual Studio, ele fornece a maioria dos mesmos recursos. Para estender o editor, use o MEF Managed Extensibility Framework ().  
  
 O SDK do Visual Studio fornece adaptadores conhecidos como *shims* para dar suporte a VSPackages que foram escritos para versões anteriores. No entanto, se você tiver um VSPackage existente, recomendamos que você atualize para a nova tecnologia para obter melhor desempenho e confiabilidade.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introdução ao uso de modelos de item do Editor.|  
|[Estender o editor e os serviços de linguagem](../extensibility/extending-the-editor-and-language-services.md)|Links para documentos que apresentam o design e os recursos do editor de núcleo e mostram como estendê-lo.|  
|[Interfaces herdadas no editor](../extensibility/legacy-interfaces-in-the-editor.md)|Links para documentos que explicam como acessar o editor principal do código existente.|  
|[Criar designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Links para documentos que explicam como criar editores personalizados.|  
|[Extensibilidade do serviço de linguagem herdado](../extensibility/internals/legacy-language-service-extensibility.md)|Contém links para documentos que descrevem como integrar a linguagens de programação no Visual Studio.|  
|[MEF (Managed Extensibility Framework)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Apresenta o Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Apresenta o Windows Presentation Foundation (WPF).|

