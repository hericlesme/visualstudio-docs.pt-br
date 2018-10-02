---
title: IDebugObject::GetSize | Microsoft Docs
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
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b58dc47a8ab10271ad2d3af20abbaa7e58b20ee7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460476"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugObject::GetSize](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-getsize).  
  
Obtém o tamanho do objeto em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pnSize`  
 [out] Retorna o tamanho em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Use o [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) método para recuperar o valor como uma sequência de bytes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

