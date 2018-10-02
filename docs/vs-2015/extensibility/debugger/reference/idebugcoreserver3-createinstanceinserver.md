---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8536fe85e58d3c43784d52b85d50015225068141
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474830"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugCoreServer3::CreateInstanceInServer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver).  
  
Cria uma instância de um mecanismo de depuração no servidor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [in] Caminho para a dll que implementa o CLSID especificado no `clsidObject` parâmetro. Quando se trata `NULL`, em seguida, COM `CoCreateInstance` função é chamada.  
  
 `wLangId`  
 [in] Localidade do mecanismo de depuração. Isso pode ser 0 se a [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) método não deve ser chamado.  
  
 `clsidObject`  
 [in] CLSID do mecanismo de depuração para criar.  
  
 `riid`  
 [in] ID de interface de uma interface específica para recuperar a partir do objeto de classe.  
  
 `ppvObject`  
 [out] `IUnknown` interface do objeto instanciado. Converter ou empacotar esse objeto para a interface desejada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)

