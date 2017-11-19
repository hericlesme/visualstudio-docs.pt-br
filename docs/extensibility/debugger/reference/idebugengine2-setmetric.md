---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2:::SetMetric
helpviewer_keywords: IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 125cedb79be629e6024e90afef16b34e57d94571
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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