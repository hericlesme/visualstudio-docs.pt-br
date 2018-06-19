---
title: Portas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a350e0579f7e60d8a7ffc3e879d79364cfdf0317
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099438"
---
# <a name="ports"></a>Portas
Em termos de arquitetura do depurador, um **porta**:  
  
-   Um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão para um dispositivo baseado em Windows CE por um cabo serial ou a uma máquina não-DCOM em rede. Uma porta especial, chamada de porta local, contém todos os processos em execução no computador local.  
  
-   Pode identificar-se por nome ou identificador.  
  
-   Pode enumerar todos os processos em execução na porta e iniciar e encerrar estes processos.  
  
-   É representado por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, que é criado, passando um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argumento [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Fornece uma porta padrão que trata os processos de todos os baseados em Windows, gerenciados e nativos. Uma porta personalizada deve ser implementada para conexões com dispositivos externos que não são baseados em Windows. Para fornecer essas portas personalizadas, um fornecedor de porta personalizado também precisa ser implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processos](../../extensibility/debugger/processes.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)