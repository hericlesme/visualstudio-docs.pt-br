---
title: IEnumDebugPortSuppliers2::Reset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPortSuppliers2::Next
helpviewer_keywords: IEnumDebugPortSuppliers2::Next
ms.assetid: f69cbacf-da9d-4b22-b8a2-abd9b8c131f2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a8b615656e9e42c1f907f3782533b02529f8eeb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugportsuppliers2reset"></a>IEnumDebugPortSuppliers2::Reset
Redefine a enumeração para o primeiro elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que este método é chamado, a próxima chamada para o [próximo](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md) método retorna o primeiro elemento da enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)