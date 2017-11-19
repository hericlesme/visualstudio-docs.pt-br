---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71cc6524a5d30e2789909a64f8b814ddb4fe286a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Sinaliza o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] da interface do usuário para avisar o usuário que símbolos não podem ser localizados para o executável iniciado no depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado por mecanismos de depuração e consumido pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] da interface do usuário do depurador.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll