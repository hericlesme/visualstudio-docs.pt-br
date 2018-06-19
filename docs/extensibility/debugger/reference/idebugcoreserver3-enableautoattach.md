---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf32eb5d8771f95ec155a93d1fe1e770e0cc2d52
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108489"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Habilita a anexação automática para os mecanismos de depuração especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rgguidSpecificEngines`  
 [in] Matriz de GUIDs para cada mecanismo de depuração para marcar como anexar automaticamente.  
  
 `celtSpecificEngines`  
 [in] O número de mecanismos especificado em `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] A URL inicial a ser usado ao conectar automaticamente.  
  
 `pbstrSessionID`  
 [out] ID da sessão que foi anexado automaticamente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna o código de erro. Um código de erro é `E_AUTO_ATTACH_NOT_REGISTERED`, que indica que a fábrica de classe auto-attach não foi registrada.  
  
## <a name="remarks"></a>Comentários  
 Quando um programa associado a URL especificada é iniciado, os mecanismos de depuração especificado são automaticamente iniciados e anexados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)