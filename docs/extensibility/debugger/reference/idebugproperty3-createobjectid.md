---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df4e45c442745652b3305fd91146bd31ffe79e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120969"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Cria uma ID exclusiva para essa propriedade para garantir que ele seja exclusivo entre todas as outras propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado quando deseja que o Gerenciador de sessão de depuração certificar-se de que essa propriedade é identificada exclusivamente entre todas as outras propriedades. O mecanismo de depuração (DE) oferece suporte a esse método, a menos que as propriedades que ela trata já exclusivamente são identificadas. Se o DE não dá suporte a esse método, ele retorna `E_NOTIMPL`.  
  
 Nenhum ID exclusivo criado com `CreateObjectID` é destruída quando o [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) é chamado de método; isso também sinaliza o término da necessidade para identificar exclusivamente essa propriedade.  
  
> [!NOTE]
>  Não há nenhum método para recuperar essa ID exclusiva, por isso o DE fazer o que quiser para identificações exclusivas quando o `CreateObjectID` método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)