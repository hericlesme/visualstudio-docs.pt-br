---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords: IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 799ac5ee39322579ab60901ffe2abb2f2a683138
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Este método adiciona um nó de programa para cada mecanismo de depuração (DE) especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidLaunchingEngine`  
 [in] O `GUID` de um DE que deve ser usado para iniciar programas (e é considerado como para adicionar seus próprios nós de programa).  
  
 `rgguidSpecificEngines`  
 [in] Matriz de `GUID`s de DEs para o programa que nós serão adicionados.  
  
 `celtSpecificEngines`  
 [in] O número de `GUID`s a `rgguidSpecificEngines` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 [Nós de programa](../../../extensibility/debugger/program-nodes.md) será adicionada para cada ir listada em `rgguidSpecificEngines`— exceto o mecanismo de inicialização (conforme fornecido no `guidLaunchingEngine`), que é assumido para adicionar seu próprio nó de programa quando ele inicia um programa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nós de programa](../../../extensibility/debugger/program-nodes.md)