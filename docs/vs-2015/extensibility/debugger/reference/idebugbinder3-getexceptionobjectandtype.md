---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
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
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ae8635e1b0888b40d668040959cade3c900f04d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462587"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBinder3::GetExceptionObjectAndType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype).  
  
Esse método recupera a exceção associada a um objeto, se houver.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppException`  
 [out] Retorna o objeto que representa a exceção.  
  
 `ppField`  
 [out] Retorna o objeto que representa um campo específico que pode ter causado a exceção (Isso pode ser um valor nulo).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
> [!NOTE]
>  Para verificar se há uma exceção, verifique o valor retornado por `ppException`: se ele for um valor nulo, nenhuma exceção está associada este objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

