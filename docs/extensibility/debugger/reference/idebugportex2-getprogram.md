---
title: IDebugPortEx2::GetProgram | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetProgram
helpviewer_keywords:
- IDebugPortEx2::GetProgram
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 750c0923db67a2e8c67dc2dc9e8793606653d691
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113689"
---
# <a name="idebugportex2getprogram"></a>IDebugPortEx2::GetProgram
Obtém o programa associado a um nó de programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProgram(   
   IDebugProgramNode2* pProgramNode,  
   IDebugProgram2**    ppProgram  
);  
```  
  
```csharp  
int GetProgram(   
   IDebugProgramNode2 pProgramNode,  
   out IDebugProgram2 ppProgram  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProgramNode`  
 [in] Um [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa o nó do programa.  
  
 `ppProgram`  
 [out] Retorna um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa associado ao nó de programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)