---
title: Comando roteamento VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58be191a3b7a2256d0883e313f77b264f6be4d69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135773"
---
# <a name="command-routing-in-vspackages"></a>Roteamento de comando em VSPackages
Um comando é roteado em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com base no contexto no qual ele é executado. Ela é roteada do contexto inicial para fora de contexto global.  
  
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