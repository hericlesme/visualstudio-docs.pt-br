---
title: Servidores (Visual Studio SDK) | Microsoft Docs
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
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476294"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK do Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [servidores (SDK do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk).  
  
Em termos de arquitetura do depurador, uma **server**:  
  
-   É um contêiner de portas e os fornecedores de porta e é usado para comunicar-se as portas e os fornecedores de porta para o Gerenciador de sessão de depuração (SDM) e mecanismos de depuração.  
  
-   Pode identificar-se por nome e enumerar suas portas e os fornecedores de porta.  
  
-   É representado por um [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, que só é implementada pelo Visual Studio (uma instância de um servidor para cada instância de execução do Visual Studio).  
  
## <a name="see-also"></a>Consulte também  
 [Portas](../../extensibility/debugger/ports.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

