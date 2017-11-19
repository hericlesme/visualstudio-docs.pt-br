---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Retorna uma estrutura que descreve um objeto e seu local em seu escopo ou contêiner.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [out no] Um [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura é preenchida por este método.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura é passada para este método, que preenche com as informações apropriadas. Como essas informações são interpretadas depende do tipo de informações retornadas e o manipulador de símbolo em si. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obter mais detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)