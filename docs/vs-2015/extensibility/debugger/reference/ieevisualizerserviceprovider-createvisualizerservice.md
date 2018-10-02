---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
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
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cf31da1dab9e53a1c473ee8024a7fe1cb9a5f2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473158"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IEEVisualizerServiceProvider::CreateVisualizerService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice).  
  
Esse método cria um serviço de visualização simultânea.  
  
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
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `binder`, `pSymProv`, e `pAddress` parâmetros foram passados para o `IDebugParsedExpression::EvaluateSync` método. `CreateVisualizerService` deve ser chamado apenas de `IDebugParsedExpression::EvaluateSync` como parte de suporte de um avaliador de expressão para visualizadores de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

