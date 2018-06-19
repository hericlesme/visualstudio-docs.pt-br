---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d24665526f4487f6d2f514f41eb2afbc291847c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108304"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera o identificador para o domínio de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pappDomainId`  
 [out] Retorna o identificador de domínio de aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As alterações de identificador de domínio de aplicativo sempre que o aplicativo é reiniciado e um novo domínio de aplicativo é criado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)