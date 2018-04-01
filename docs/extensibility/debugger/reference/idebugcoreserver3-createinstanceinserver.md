---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cbd287f5ab75374a3272ecbb34c36ffdf384ba84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Cria uma instância de um mecanismo de depuração no servidor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szDll`  
 [in] Caminho para a dll que implementa o CLSID especificado no `clsidObject` parâmetro. Se isso for `NULL`, em seguida, COM `CoCreateInstance` função é chamada.  
  
 `wLangId`  
 [in] Localidade do mecanismo de depuração. Isso pode ser 0 se o [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) método não deve ser chamado.  
  
 `clsidObject`  
 [in] CLSID do mecanismo de depuração para criar.  
  
 `riid`  
 [in] ID de interface de uma interface específica para recuperar o objeto de classe.  
  
 `ppvObject`  
 [out] `IUnknown` interface do objeto instanciado. Converter ou empacotar este objeto para a interface desejado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)