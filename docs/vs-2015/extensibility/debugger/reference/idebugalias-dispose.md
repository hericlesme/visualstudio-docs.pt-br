---
title: IDebugAlias::Dispose | Microsoft Docs
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
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6032612d021e257a9f2c8ef74d35f3bec4a343a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463246"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugAlias::Dispose](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias-dispose).  
  
Marca este alias para remoção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que esse método é chamado, o alias não está mais disponível.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

