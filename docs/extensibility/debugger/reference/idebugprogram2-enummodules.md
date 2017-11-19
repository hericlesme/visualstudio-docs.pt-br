---
title: IDebugProgram2::EnumModules | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::EnumModules
helpviewer_keywords: IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23f905a4a7fc239efb2220f15deb95954a46d998
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Recupera uma lista de módulos que esse programa foi carregado e está em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumModules(   
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int EnumModules(   
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) objeto que contém uma lista dos módulos.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um módulo é uma DLL ou assembly e normalmente é listado no **módulos** janela de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)