---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b17d75ace19ac53cbcd229d7c15de573c1ecb8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114502"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Grava um despejo de memória em um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `DumpType`  
 [in] Um valor da [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumeração que especifica o tipo de despejo de memória, por exemplo, curto ou longo.  
  
 `pszDumpUrl`  
 [in] A URL para gravar o despejo de memória para. Normalmente, isso é na forma de `file://c:\path\filename.ext`, mas pode ser qualquer URL válido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um despejo de memória de programa normalmente inclui o quadro de pilhas atual, a pilha em si, uma lista dos threads em execução no programa e possivelmente toda a memória que possui o programa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)