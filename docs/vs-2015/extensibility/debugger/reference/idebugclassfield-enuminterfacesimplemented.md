---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
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
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9c21a20fc832a42baa7386f50289d8297a3e34f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466827"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugClassField::EnumInterfacesImplemented](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented).  
  
Cria um enumerador para as interfaces implementadas por esta classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhuma interface implementado nesta classe. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que descreve uma interface. Observe que não gerenciados [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] código não usa interfaces como uma entidade separada para que esse método sempre retorna um valor nulo para não gerenciado [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] código.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

