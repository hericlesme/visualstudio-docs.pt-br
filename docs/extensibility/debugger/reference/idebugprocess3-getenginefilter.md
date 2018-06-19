---
title: IDebugProcess3::GetEngineFilter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetEngineFilter
- IDebugProcess3::GetEngineFilter
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c592220267444818f7310895974b92cd02c69a62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122282"
---
# <a name="idebugprocess3getenginefilter"></a>IDebugProcess3::GetEngineFilter
Recupera uma matriz de identificadores exclusivos para mecanismos de depuração disponíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```csharp  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pEngineArray`  
 [out] Referência a uma estrutura que contém identificadores exclusivos para mecanismos de depuração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)