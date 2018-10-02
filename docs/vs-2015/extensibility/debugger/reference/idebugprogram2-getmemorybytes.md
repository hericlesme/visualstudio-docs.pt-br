---
title: IDebugProgram2::GetMemoryBytes | Microsoft Docs
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
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af197f9289e255504da91dc9564cad87ec8e960d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462850"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgram2::GetMemoryBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getmemorybytes).  
  
Recupera os bytes de memória ocupados pelo programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppMemoryBytes`  
 [out] Retorna um [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto que representa os bytes de memória do programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os bytes de memória, conforme representado pela [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto é para a imagem do programa na memória e não qualquer memória que foi atribuída quando o programa foi executado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)

