---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 701c5e33273dc6d00156e554e1abaa9a003568eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Esse método é chamado para exibir o valor especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hwnd`  
 [in] Janela pai  
  
 `dwID`  
 [in] ID de visualizadores personalizados que oferecem suporte a mais de um tipo.  
  
 `pHostServices`  
 [in] Reservado. Sempre definido como null.  
  
 `pDebugProperty`  
 [in] Interface que pode ser usado para recuperar o valor a ser exibido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna o código de erro.  
  
## <a name="remarks"></a>Comentários  
 A exibição é "restrita" em que esse método criar a janela necessária, exibir o valor, aguardar a entrada e feche a janela, todos os antes de retornar ao chamador. Isso significa que o método deve tratar todos os aspectos de exibir o valor da propriedade, da criação de uma janela de saída, a espera pela entrada do usuário, ao destruir a janela.  
  
 Para dar suporte a alteração do valor na determinado [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) do objeto, você pode usar o [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) método — se o valor pode ser expressa como uma cadeia de caracteres. Caso contrário, será necessário criar uma interface personalizada — exclusivo para o avaliador de expressão implementar isso `DisplayValue` método — no mesmo objeto que implementa o `IDebugProperty3` interface. Essa interface personalizada fornece métodos para alterar os dados de um tamanho arbitrário ou complexidade.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)