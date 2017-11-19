---
title: IDebugEngine2::SetLocale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::SetLocale
helpviewer_keywords: IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41ad173f706b655f4d43a101618127070ae9ac6e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Define a localidade do mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wLangID`  
 [in] Especifica a localidade do idioma. Por exemplo, 1033 para inglês.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado, o Gerenciador de sessão de depuração (SDM) a propagação das configurações de localidade do IDE para que as cadeias de caracteres retornadas por DE corretamente estão localizadas.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)