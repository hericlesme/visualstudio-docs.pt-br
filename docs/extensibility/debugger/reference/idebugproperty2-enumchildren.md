---
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9631ee89dc9d241932b745db4ce094799a899bad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera uma lista de filhos da propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeração que especifica quais campos o enumerado [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas devem ser preenchidos.  
  
 `dwRadix`  
 [in] Especifica a base a ser usada na formatação de todas as informações numéricas.  
  
 `guidFilter`  
 [in] GUID do filtro usado com o `dwAttribFilter` e `pszNameFilter` parâmetros para selecionar qual `DEBUG_PROPERTY_INFO` filhos são a serem enumerados. Por exemplo, `guidFilterLocals` filtros para variáveis locais.  
  
 `dwAttribFilter`  
 [in] Uma combinação de sinalizadores do [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeração que especifica o tipo de objetos a serem enumerados, por exemplo `DBG_ATTRIB_METHOD` para todos os métodos que podem ser filhos dessa propriedade. Usado em combinação com o `guidFilter` e `pszNameFilter` parâmetros.  
  
 `pszNameFilter`  
 [in] O nome do filtro usado com o `guidFilter` e `dwAttribFilter` parâmetros para selecionar qual `DEBUG_PROPERTY_INFO` filhos são a serem enumerados. Por exemplo, definir esse parâmetro como "MyX" filtros para todos os filhos com o nome "MyX".  
  
 `dwTimeout`  
 [in] Especifica o tempo máximo, em milissegundos, de espera antes de retornar desse método. Use `INFINITE` aguardar indefinidamente.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contém uma lista das propriedades filho.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)