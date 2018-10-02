---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
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
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f821c72259a77618c6cd83fe6df84837e21a6db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462622"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPortSupplier3::EnumPersistedPorts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier3-enumpersistedports).  
  
Esse método recupera um objeto que permite a enumeração da lista de portas persistentes.  
  
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
 [in] Um [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) estrutura que contém uma lista de nomes de porta para encontrar e retornar entre as portas persistentes. Somente as portas persistentes com esses nomes serão retornadas.  
  
 `ppEnum`  
 [out] Um objeto que implementa o [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Portas persistentes são carregadas quando um fornecedor de porta é instanciado e salvo quando o fornecedor de porta é destruído.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)

