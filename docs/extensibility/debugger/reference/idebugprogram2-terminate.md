---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Encerra o programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se possível, o programa será encerrado e descarregado do processo; Caso contrário, o mecanismo de depuração (DE) executará qualquer limpeza necessária.  
  
 Este método ou o [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) método é chamado pelo IDE, normalmente em resposta ao usuário parar a depuração de todas as. A implementação desse método deve, idealmente, terminá-lo dentro do processo. Se isso não for possível, o DE deve impedir que o programa seja executado mais neste processo (e fazer qualquer limpeza necessária). Se o `IDebugProcess2::Terminate` método foi chamado pelo IDE, todo o processo será encerrado em algum momento após o `IDebugProgram2::Terminate` método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)