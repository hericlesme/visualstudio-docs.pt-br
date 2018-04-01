---
title: IDebugReference2::EnumChildren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7d30838a353f5bf113cc403a8caae6486c595183
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Obter uma lista de filhos selecionados de uma referência. Reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumeração que especifica quais campos o enumerado [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estruturas devem ser preenchidos.  
  
 `dwRadix`  
 [in] A base a ser usada na formatação de todas as informações numéricas.  
  
 `dwAttribFilter`  
 [in] Uma combinação de sinalizadores do [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeração é usada como um filtro em combinação com o `pszNameFilter` parâmetro para selecionar quais estruturas estão a serem enumerados.  
  
 `pszNameFilter`  
 [in] Uma cadeia de caracteres especificando um filtro, como "MyX", usado em combinação com o `dwAttribFilter` parâmetro para selecionar as estruturas a serem enumerados.  
  
 `dwTimeout`  
 [in] Tempo máximo, em milissegundos, de espera antes de retornar desse método. Use `INFINITE` aguardar indefinidamente.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) objeto que contém uma lista das propriedades filho solicitada.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)