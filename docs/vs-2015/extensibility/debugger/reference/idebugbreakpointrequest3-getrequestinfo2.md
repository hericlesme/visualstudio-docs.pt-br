---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs
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
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62c04aef42571eebe96e2f03b3cc99eedd8e7b3e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476278"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBreakpointRequest3::GetRequestInfo2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2).  
  
Esse método obtém as informações de solicitação de ponto de interrupção que descreve esta solicitação de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```csharp  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeração que determinam quais campos de `pBPRequestInfo` devem ser preenchidos.  
  
 `bBPRequestInfo`  
 [out] O [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura a ser preenchido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Há mais informações nesta solicitação que é retornado a partir de [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)

