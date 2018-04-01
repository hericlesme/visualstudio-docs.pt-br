---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6b493229ab33f628c54580711604b16a4e2b5c5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Verifica se um fornecedor de porta pode adicionar novas portas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna se a porta pode ser adicionada, `S_OK`; caso contrário, retorna `S_FALSE` para indicar que nenhuma porta pode ser adicionada a este fornecedor de porta.  
  
## <a name="remarks"></a>Comentários  
 Chamar esse método antes de chamar o [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) método desde o último método cria a porta, bem como adicionar, que pode ser uma operação demorada.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)