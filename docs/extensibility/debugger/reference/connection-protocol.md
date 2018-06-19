---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e1dc8cd22b529eafd6183578be7de6ffe69549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109997"
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