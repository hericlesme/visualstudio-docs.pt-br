---
title: IDebugCoreServer2::EnumPortSuppliers | Microsoft Docs
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
- IDebugCoreServer2::EnumPortSuppliers
helpviewer_keywords:
- IDebugCoreServer2::EnumPortSuppliers
ms.assetid: ce0c90e4-8e02-4b08-b558-7677fb2c88f7
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c4d34ceee41d64ddab409d1cea25a72da0c794f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465736"
---
# <a name="idebugcoreserver2enumportsuppliers"></a>IDebugCoreServer2::EnumPortSuppliers
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugCoreServer2::EnumPortSuppliers](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers).  
  
Recupera uma lista de todos os fornecedores de porta disponível.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumPortSuppliers(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int EnumPortSuppliers(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) objeto que contém uma lista de todos os fornecedores de porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)

