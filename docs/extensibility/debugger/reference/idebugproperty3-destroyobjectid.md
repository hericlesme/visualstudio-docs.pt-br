---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0db5ef80a1734aedb819c109aa4c27c40224886e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Destrói a ID exclusiva associada a essa propriedade, indicando que o chamador não se importa identificar essa propriedade exclusivamente de todas as outras propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se o mecanismo de depuração não precisa oferecer suporte a IDs exclusivas para uma propriedade (porque ele já rastreia exclusivamente internamente), em seguida, ele pode simplesmente retornar `E_NOTIMPL` para este método.  
  
 IDs exclusivos são criados com uma chamada para o [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) método quando quiser que o chamador certificar-se de que essa propriedade é identificada exclusivamente entre todas as outras propriedades.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)