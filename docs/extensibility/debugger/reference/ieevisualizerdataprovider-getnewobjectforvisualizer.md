---
title: IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7025acd33aad7dddf947f5a151d4980fbe64a823
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
Esse método obtém um novo objeto para o visualizador. Esse método sempre criará um novo objeto do objeto existente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNewObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetNewObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppObject`  
 [out] O novo objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 `This method` avalia novamente o objeto representa atualmente e retorna o resultado como um novo objeto. O objeto existente será atualizado como resultado da avaliação.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)