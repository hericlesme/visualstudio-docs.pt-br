---
title: IDebugProperty2::GetPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f922731f5c595f7308f78269b8386b7da20e2398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Obtém o [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estrutura que descreve uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de valores da [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeração que especifica quais campos devem ser preenchidas no `pPropertyInfo` estrutura.  
  
 `nRadix`  
 [in] Base a ser usada na formatação de todas as informações numéricas.  
  
 `dwTimeout`  
 [in] Especifica o tempo máximo, em milissegundos, de espera antes de retornar desse método. Use `INFINITE` aguardar indefinidamente.  
  
 `rgpArgs`  
 [out no] Reservado para uso futuro; definido como um valor nulo.  
  
 `dwArgCount`  
 [in] Reservado para uso futuro; definido como zero.  
  
 `pPropertyInfo`  
 [out] Um [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estrutura que é preenchida com a descrição da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)