---
title: IEnumDebugModules2::Clone | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugModules2::Clone
helpviewer_keywords: IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbeb94a2cbdfbbe04893ed491287057639d3949d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugModules2 ppEnum  
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
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)