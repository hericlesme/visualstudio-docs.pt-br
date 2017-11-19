---
title: IDebugModOpt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa4416bbb2a4b37ba986bb0d57b32dfa5aa319cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa um modificador opcional de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obtido um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa uma classe ou método.  
  
## <a name="methods"></a>Métodos  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera uma lista dos modificadores opcionais.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll