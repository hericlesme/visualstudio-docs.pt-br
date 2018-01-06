---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONNECTION_PROTOCOL
helpviewer_keywords: CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ff7a1f97304dd9ba09dc8f44f3d05a23196fdeb1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Indica o protocolo usado para comunicação entre um servidor de depuração e o pacote de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 CONNECTION_NONE  
 Nenhuma conexão foi feita em um servidor.  
  
 CONNECTION_UNKNOWN  
 Foi feita uma conexão, mas ele é de um tipo desconhecido.  
  
 CONNECTION_LOCAL  
 Conexão é um servidor local.  
  
 CONNECTION_PIPE  
 Conexão é por meio de um pipe nomeado.  
  
 CONNECTION_TCPIP  
 Conexão usa TCP/IP.  
  
 CONNECTION_HTTP  
 Conexão usa HTTP (por meio de um servidor Web).  
  
 CONNECTION_OTHER  
 Algum outro tipo de conexão foi estabelecido (esse valor não é atualmente usado).  
  
## <a name="remarks"></a>Comentários  
 Esses valores são retornados do [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)