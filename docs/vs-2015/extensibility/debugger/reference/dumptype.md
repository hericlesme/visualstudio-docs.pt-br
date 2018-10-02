---
title: DUMPTYPE | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1548ca9205776e5a9677962bf620a350ede6c64e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464377"
---
# <a name="dumptype"></a>DUMPTYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [DUMPTYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/dumptype).  
  
Especifica a quantidade de estado de um programa (como threads em execução, quadros de pilha e o endereço da instrução atual) para despejo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Membros  
 DUMP_MINIDUMP  
 Especifica um despejo de pequeno e compacto.  
  
 DUMP_FULLDUMP  
 Especifica um despejo completo, grande.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)

