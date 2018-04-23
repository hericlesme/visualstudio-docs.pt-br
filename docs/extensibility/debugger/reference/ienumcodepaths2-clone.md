---
title: IEnumCodePaths2::Clone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2::Clone
helpviewer_keywords:
- IEnumCodePaths2::Clone
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7466051b7dd541e4361feb654c4ae5dfcd3c21bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ienumcodepaths2clone"></a>IEnumCodePaths2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Clone(  
   IEnumCodePaths2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumCodePaths2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna uma cópia dessa enumeração como um objeto separado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cópia da enumeração tem o mesmo estado original no momento em que este método é chamado. No entanto, o original e da cópia estados são separados e podem ser alterados individualmente.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)