---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 974b76bafabaa3621ffb71a530b67e9643436c04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Esse método obtém a atualização de editar e continuar (c) para este programa. Um mecanismo de depuração personalizado sempre retorna `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUpdate`  
 [out] Retorna uma interface interna que pode ser usada para atualizar este programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
> [!NOTE]
>  Um mecanismo de depuração personalizado deve sempre retornar `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)