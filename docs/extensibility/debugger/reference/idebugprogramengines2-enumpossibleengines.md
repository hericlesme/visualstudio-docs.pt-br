---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d30eb28398569aa3d14b4a7dd363abac785f352c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Retorna os GUIDs para todos os possíveis mecanismos de depuração (DE) que podem depurar este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celtBuffer`  
 [in] O número DE GUIDs para retornar. Isso também especifica o tamanho máximo da `rgguidEngines` matriz.  
  
 `rgguidEngines`  
 [out no] Uma matriz DE GUIDs devem ser preenchidos.  
  
 `pceltEngines`  
 [out] Retorna o número real DE GUIDs que são retornados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [c#] 0x8007007A se o buffer não é grande o suficiente.  
  
## <a name="remarks"></a>Comentários  
 Para determinar quantos mecanismos existe, chame este método uma vez com o `celtBuffer` parâmetro definido como 0 e o `rgguidEngines` parâmetro definido como um valor nulo. Isso retorna `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para c#) e o `pceltEngines` parâmetro retorna o tamanho necessário do buffer.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)