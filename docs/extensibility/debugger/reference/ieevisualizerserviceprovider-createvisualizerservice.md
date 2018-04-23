---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f59d86e94be5c0295786b747f6b57753aa087b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Esse método cria um serviço do visualizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `binder`  
 [in] O [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto passado para [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] O [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto passado para `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] O [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto passado para `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Um objeto que implementa o [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface (fornecido pelo avaliador de expressão).  
  
 `ppService`  
 [out] O serviço criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `binder`, `pSymProv`, e `pAddress` parâmetros foram passados para o `IDebugParsedExpression::EvaluateSync` método. `CreateVisualizerService` deve ser chamado apenas de `IDebugParsedExpression::EvaluateSync` como parte de suporte de um avaliador de expressão para visualizadores de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)