---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84110c4e7d6a3e940df587811c24d4316f786cf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
PRETERIDO. NÃO USE.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Uma implementação deve retornar sempre `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentários  
  
> [!WARNING]
>  Como de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], esse método não é mais usado e deve retornar sempre `E_NOTIMPL`.  
  
 Esse método é chamado quando o depurador inesperadamente. Quando este método é chamado, o DE deverá continuar o programa que o usuário desanexado dele. Não há mais eventos de depuração devem ser enviados. O programa deve estar em um estado em que ele é anexável de outra instância do depurador.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)