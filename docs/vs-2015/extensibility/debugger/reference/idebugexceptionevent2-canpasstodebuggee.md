---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
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
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7233d6ee9b1f82d72717df9284221fca65673391
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475381"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugExceptionEvent2::CanPassToDebuggee](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee).  
  
Determina se o mecanismo de depuração (DES) oferece suporte a opção de passar essa exceção para o programa que está sendo depurado quando a execução é retomada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um `S_OK` (a exceção pode ser passada para o programa) ou `S_FALSE` (a exceção não pode ser passada).  
  
## <a name="remarks"></a>Comentários  
 O DE deve ter uma ação padrão para passar para o elemento a ser depurado. O IDE pode receber o [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento e a chamada a [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método sem chamar o `CanPassToDebuggee` método. Portanto, o DE deve ter um caso de padrão para transmitir a exceção na ou não.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

