---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords: IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49f76fe661ec718759600771149f5363788d3a85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Esse método retorna um objeto que permite a enumeração da lista de portas persistentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `PortNames`  
 [in] Um [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) estrutura que contém uma lista de nomes de porta para localizar e retornar entre as portas persistentes. Somente as portas persistentes com esses nomes serão retornadas.  
  
 `ppEnum`  
 [out] Um objeto que implementa o [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Portas persistentes são carregadas quando um fornecedor de porta é instanciado e salvo quando o fornecedor de porta é destruído.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)