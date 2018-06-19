---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91e4c4648108cdc6afa28f5a5dd8f9bfd46fcf59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126341"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Descreve ou especifica as propriedades de um processo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="members"></a>Membros

PIFLAG_SYSTEM_PROCESS  
Indica que o processo é um processo do sistema.

PIFLAG_DEBUGGER_ATTACHED  
Indica que o processo está sendo depurado por um depurador. Pode ser um [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador, ou pode ser algum outro depurador, por exemplo, WinDbg.

PIFLAG_PROCESS_STOPPED  
Indica que o processo será interrompido. Válido somente se `PIFLAG_DEBUGGER_ATTACHED` também for especificado. Disponível no Visual Studio 2005 e versões posteriores.

PIFLAG_PROCESS_RUNNING  
Indica que o processo está sendo executado. Válido somente se `PIFLAG_DEBUGGER_ATTACHED` também for especificado. Disponível no Visual Studio 2005 e versões posteriores.

## <a name="remarks"></a>Comentários

Usado para o `Flags` membro o [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estrutura.

Esses sinalizadores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos

Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também

[Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)