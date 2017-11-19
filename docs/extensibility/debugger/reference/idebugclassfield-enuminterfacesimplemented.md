---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords: IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ed2acbae6331829dca351ec7b90ae5bea9981a3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Cria um enumerador para as interfaces implementadas por esta classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de interfaces implementadas. Retorna um valor nulo se não houver nenhuma interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver nenhuma interfaces implementadas nessa classe. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é uma [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que descreve uma interface. Observe que não gerenciado [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] código não usa interfaces como uma entidade separada para esse método sempre retorna um valor nulo para não gerenciado [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] código.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)