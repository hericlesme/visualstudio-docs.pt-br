---
title: IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b972885a8999ac688ade380fbe9601d4274d205e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Esse método obtém o tipo de campo de classe que representa um nome de classe totalmente qualificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClassTypeByName(   
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IDebugClassField** ppField  
);  
```  
  
```csharp  
int GetClassTypeByName(  
   string               pszClassName,   
   NAME_MATCH           nameMatch,   
   out IDebugClassField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszClassName`  
 [in] O nome da classe.  
  
 `nameMatch`  
 [in] Seleciona o tipo de correspondência, por exemplo, diferencia maiusculas de minúsculas. Um valor da [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumeração.  
  
 `ppField`  
 [out] Retorna o tipo de classe, conforme representado pelo [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)