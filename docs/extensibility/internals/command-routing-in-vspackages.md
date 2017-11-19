---
title: Comando roteamento VSPackages | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffbfb131eedb316c321bbf955ec7cc2951c71b8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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