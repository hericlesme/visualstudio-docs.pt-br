---
title: Roteamento em VSPackages de comando | Microsoft Docs
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
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e945b16134debce8ec23ed15e5c9b0ca436e5bd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474631"
---
# <a name="command-routing-in-vspackages"></a>Roteamento de comando em VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [roteamento de comando em VSPackages](https://docs.microsoft.com/visualstudio/extensibility/internals/command-routing-in-vspackages).  
  
Um comando é roteado em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] baseado no contexto no qual ele é executado. Ela é roteada do contexto inicial para fora para o contexto global.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md)  
 Descreve a ordem de resolução de roteamento de comando.  
  
 [Disponibilidade](../../extensibility/internals/command-availability.md)  
 Discute o roteamento de comando.  
  
 [Comandos e menus que usam assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Discute considerações em comandos de roteamento entre código gerenciado e COM.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Objetos do contexto de seleção](../../extensibility/internals/selection-context-objects.md)  
 Discute o modelo de como você pode determinar o foco de contexto de seleção do usuário em uma janela.  
  
 [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica como criar uma interface do usuário que inclui menus, barras de ferramentas e caixas de combinação de comando.

