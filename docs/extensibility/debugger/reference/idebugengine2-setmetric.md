---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 49208b4ef01d3f1a8cc22abe6d9a926089febed1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Esse método define um valor de registro conhecido como uma métrica.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszMetric`  
 [in] O nome da métrica.  
  
 `varValue`  
 [in] Especifica o valor de métrica.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma métrica é um valor do registro usado para alterar o comportamento de um mecanismo de depuração ou anunciar funcionalidade com suporte. Esse método pode encaminhar a chamada para o formato apropriado do [auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) função `SetMetric`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)