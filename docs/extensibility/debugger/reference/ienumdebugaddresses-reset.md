---
title: IEnumDebugAddresses::Reset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::Reset
helpviewer_keywords: IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b126565533bc46c315502ddce06f95f1d588271a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Este método redefine a enumeração para o primeiro elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que este método é chamado, a próxima chamada para [próximo](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) retorna o primeiro elemento da enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)