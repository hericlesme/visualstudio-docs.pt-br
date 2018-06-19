---
title: Servidores (SDK do Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2904641e8188abc6ef2382b2da272a9f96fd0f81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125486"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK do Visual Studio)
Em termos de arquitetura do depurador, um **server**:  
  
-   É um contêiner de portas e os fornecedores de porta e é usado para se comunicar portas e os fornecedores de porta para o Gerenciador de sessão de depuração (SDM) e mecanismos de depuração.  
  
-   Pode identificar-se por nome e enumerar suas portas e os fornecedores de porta.  
  
-   É representado por um [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, que só é implementada pelo Visual Studio (uma instância de um servidor para cada instância de execução do Visual Studio).  
  
## <a name="see-also"></a>Consulte também  
 [Portas](../../extensibility/debugger/ports.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)