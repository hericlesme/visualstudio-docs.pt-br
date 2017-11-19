---
title: IDebugErrorBreakpoint2::GetBreakpointResolution | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorBreakpoint2::GetBreakpointResolution
helpviewer_keywords: IDebugErrorBreakpoint2::GetBreakpointResolution
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ceaea149f03019df26284be9a8470bcb1ed886a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugerrorbreakpoint2getbreakpointresolution"></a>IDebugErrorBreakpoint2::GetBreakpointResolution
Obtém a resolução de erro do ponto de interrupção que descreve o erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetBreakpointResolution(   
   IDebugErrorBreakpointResolution2** ppErrorResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugErrorBreakpointResolution2 ppErrorResolution  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppErrorResolution`  
 [out] Retorna um [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) objeto que descreve o erro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)