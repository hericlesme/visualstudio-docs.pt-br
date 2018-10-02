---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
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
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69d7cfd4b7e9a0598a8240d9392f1835c30bd561
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462971"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugMemoryBytes2::WriteAt](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorybytes2-writeat).  
  
Grava o número especificado de bytes de memória, iniciando no endereço especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStartContext`  
 [in] O [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica o local iniciar a gravação de bytes.  
  
 `dwCount`  
 [in] O número de bytes a serem gravados.  
  
 `rgbMemory`  
 [in] Bytes a serem gravados. Essa matriz deve para ter pelo menos `dwCount` bytes de tamanho.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` se nem todos os bytes poderia ser escritos ou retorna um código de erro (normalmente `E_FAIL`).  
  
## <a name="remarks"></a>Comentários  
 Se o endereço inicial não está dentro da janela de memória, representada por este [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) do objeto, nenhuma gravação ocorrerá e um código de erro `E_FAIL` é retornado — mesmo que se sobreponha a quantidade para gravar no espaço de memória.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

