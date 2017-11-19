---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::EnumFrameInfo
helpviewer_keywords: IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15e775af8f04e52b5cb1329312c1e0226a14c733
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera uma lista de registros de ativação para este segmento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 [in] Uma combinação de sinalizadores do [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumeração que especifica quais campos do [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estruturas devem ser preenchidos. Especifique o `FIF_FUNCNAME_FORMAT` sinalizador para formatar o nome da função em uma única cadeia de caracteres.  
  
 `nRadix`  
 [in] Base usada na formatação informações numéricas no enumerador.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) objeto que contém uma lista de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estruturas que descreve o quadro de pilhas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quadros do thread são enumerados na ordem, com o quadro atual enumeradas primeiro e o quadro mais antigo enumerados última.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)