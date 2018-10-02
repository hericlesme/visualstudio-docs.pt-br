---
title: IDebugBreakpointChecksumRequest2::IsChecksumEnabled | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79490934757d55d26a365eab67c0aa4ee5bcbeb0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462700"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBreakpointChecksumRequest2::IsChecksumEnabled](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled).  
  
Determina se a soma de verificação está habilitada para este documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsChecksumEnabled(   
   BOOL *pfChecksumEnabled  
);  
```  
  
```csharp  
public int IsChecksumEnabled(   
   out int pfChecksumEnabled  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfChecksumEnabled`  
 [out] Retornará TRUE se a soma de verificação está habilitada; Caso contrário, retornará FALSE.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)

