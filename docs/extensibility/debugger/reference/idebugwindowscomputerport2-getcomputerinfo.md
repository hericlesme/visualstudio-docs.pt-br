---
title: IDebugWindowsComputerPort2::GetComputerInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9dff1b64cafa6a212600cd467b86f8ddca83337
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
Recupera informações sobre o computador no qual o depurador em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetComputerInfo(  
   COMPUTER_INFO * pInfo  
);  
```  
  
```csharp  
public int GetComputerInfo(  
   out COMPUTER_INFO[] pInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pInfo`  
 [out] Referência a uma estrutura que contém as informações do computador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)   
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)