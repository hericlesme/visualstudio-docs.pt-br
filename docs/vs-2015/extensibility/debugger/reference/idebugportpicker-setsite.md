---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57f3ada6c5a1b2434e5b88b077f71c678321db68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464768"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPortPicker::SetSite](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker-setsite).  
  
Define o provedor de serviço.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSP`  
 [in] Referência à interface do provedor de serviços.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método será chamado antes de quaisquer outros métodos são chamados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

