---
title: IDebugMemoryContext2::Add | Microsoft Docs
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
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 47fe65ae76f60026f08d18ce17fc48e22885e042
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462374"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugMemoryContext2::Add](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorycontext2-add).  
  
Adiciona o valor especificado para o contexto atual e retorna um novo contexto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCount`  
 [in] O valor a ser adicionado ao contexto atual.  
  
 `ppMemCxt`  
 [out] Retorna um novo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um contexto de memória é um endereço, portanto, a adição de um valor para um endereço produz um novo endereço que requer uma nova interface de contexto.  
  
 Esse método sempre deve produzir um novo contexto, mesmo se o endereço resultante está fora do espaço de memória associado a este contexto. A única exceção a isso é se nenhuma memória pode ser alocada para o novo contexto ou se `ppMemCxt` é um valor nulo (que é um erro).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

