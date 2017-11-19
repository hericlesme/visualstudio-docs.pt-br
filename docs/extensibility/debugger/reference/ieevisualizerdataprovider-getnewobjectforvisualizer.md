---
title: IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords: IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81bed6a59e9405c69f0c829f46f71b82c9988086
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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
 `This method`avalia novamente o objeto representa atualmente e retorna o resultado como um novo objeto. O objeto existente será atualizado como resultado da avaliação.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)