---
title: IDebugProcess2::CanDetach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::CanDetach
helpviewer_keywords: IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66fbf5e73639766ad27f7853e8170cd49518202f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Determina se o Gerenciador de sessão de depuração (SDM) poderá desanexar o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK.` retorna `S_FALSE` se o depurador não é possível desanexar do processo. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)