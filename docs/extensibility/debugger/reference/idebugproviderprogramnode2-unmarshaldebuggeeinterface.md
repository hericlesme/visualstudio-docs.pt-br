---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9ebadbc35ee8752e9f3b985a99155444caff5f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtém uma interface especificada nos limites do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `riid`  
 [in] GUID da interface para obter.  
  
 `ppvObject`  
 [out] Retorna o objeto que implementa a interface desejada. [C++] isso pode ser convertido diretamente para o tipo de interface desejado. [C#] usam o <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obter a interface desejada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado quando o mecanismo de depuração estiver em execução no [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] espaço de processo e o programa que está sendo depurado está em execução em seu próprio espaço de processo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)