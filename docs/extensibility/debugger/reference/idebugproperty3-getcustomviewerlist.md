---
title: IDebugProperty3::GetCustomViewerList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a98a7ca4b2f1dcf25728bd0d2e3778be2d70ada
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118392"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Obtém uma lista de visualizadores personalizados associados a essa propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celtSkip`  
 [in] O número de visualizadores de ignorar.  
  
 `celtRequested`  
 [in] O número de visualizadores para recuperar (também especifica o tamanho do `rgViewers` matriz).  
  
 `rgViewers`  
 [out no] Matriz de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) estruturas devem ser preenchidos.  
  
 `pceltFetched`  
 [out] O número real de visualizadores retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para dar suporte a visualizadores de tipo, esse método encaminha a chamada para o [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método. Se o avaliador de expressão também dá suporte a visualizadores personalizados para o tipo desta propriedade, esse método pode acrescentar os visualizadores personalizados apropriados à lista.  
  
 Consulte [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obter detalhes sobre as diferenças entre os visualizadores de tipo e visualizadores personalizados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CProperty** objeto que expõe o [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)