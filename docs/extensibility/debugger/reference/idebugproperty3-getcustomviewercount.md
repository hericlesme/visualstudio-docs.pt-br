---
title: IDebugProperty3::GetCustomViewerCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::GetCustomViewerCount
helpviewer_keywords: IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ea7eba47f909086e55dd23aa6bf81b847dbb58a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Obtém o número de visualizadores personalizados que podem estar disponíveis para essa propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcelt`  
 [out] O número de visualizadores personalizados disponíveis para esta propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para oferecer suporte a visualizadores de tipo, esse método encaminha a chamada para o [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) método. Se o avaliador de expressão também dá suporte a visualizadores personalizados para o tipo desta propriedade, este método adiciona o número de visualizadores personalizados para o valor retornado.  
  
 Para obter informações detalhadas sobre as diferenças entre os visualizadores de tipo e visualizadores personalizados, consulte [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CProperty** objeto que expõe o [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)