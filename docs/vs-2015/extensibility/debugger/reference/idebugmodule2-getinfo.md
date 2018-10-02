---
title: IDebugModule2::GetInfo | Microsoft Docs
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
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29816a5a46d529daeff47b75f1ce3b9cc8470650
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476117"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugModule2::GetInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule2-getinfo).  
  
Obtém informações sobre esse módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumeração que especificam quais campos de `pInfo` devem ser preenchidos.  
  
 `pInfo`  
 [no, out] Um [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura será preenchida com uma descrição do módulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura contém o nome do módulo que é exibido na **módulos** janela.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)

