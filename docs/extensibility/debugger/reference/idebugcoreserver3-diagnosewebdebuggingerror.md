---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0facdbd5da7d17061039e0a9e7faed2be3bbe4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Falha nas tentativas de determinar o motivo pelo qual um auto-attach.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszUrl`  
 [in] Não usado no momento; deve ser sempre definido como um valor nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Estes são os outros códigos de retorno típicos:  
  
|Código|Descrição|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Não é possível determinar por que o servidor remoto falhou ao iniciar a depuração.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Não é possível depurar em um servidor remoto, possivelmente devido a permissões insuficientes ou porque o verbo DEBUG não está habilitado.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|O servidor web foi bloqueado e está bloqueando o verbo DEBUG, que é necessário para habilitar a depuração.|  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)