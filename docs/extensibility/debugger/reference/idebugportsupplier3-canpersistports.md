---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords: IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95e62f283d2ea0411162fb0406c712f0d17a1183
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Este método determina se o fornecedor de porta pode persistir portas (por gravá-los em disco) entre chamadas do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK`Se as portas podem ser persistentes, ou `S_FALSE` para indicar que as portas não podem ser persistentes.  
  
## <a name="remarks"></a>Comentários  
 Se o fornecedor de porta pode manter portas, ele deve fazer isso quando ele é destruído e, em seguida, recarregue-los quando ela é instanciada novamente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)