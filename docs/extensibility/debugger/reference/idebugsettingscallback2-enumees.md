---
title: IDebugSettingsCallback2::EnumEEs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: add7f9b34119fb11938064598b213e26000ecb1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122048"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Enumera os avaliadores de expressão disponível considerando os identificadores de idioma e fornecedor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```csharp  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celtBuffer`  
 [in] Número de elementos de `pceltEEs` buffer.  
  
 `rgguidLang`  
 [out no] Identificador exclusivo para a linguagem de programação.  
  
 `rgguidVendor`  
 [out no] Identificador exclusivo do fornecedor.  
  
 `pceltEEs`  
 [out no] Matriz de avaliadores de expressão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)