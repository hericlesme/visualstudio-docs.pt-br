---
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 077a4422d7e8edde460e03dd2a26675df3fdd6fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Representa um provedor de símbolo que tem acesso direto a interfaces de símbolo principal e de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera o identificador de domínio de aplicativo que recebe o endereço de depuração.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera informações sobre os módulos no grupo de símbolo.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera informações sobre o grupo de símbolo do qual o provedor de símbolo é um membro.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera as informações de importação de metadados.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera informações sobre o método no endereço de depuração especificado.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera um leitor de símbolo para código não gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface pode ser usada em vez da maioria das outras interfaces de provedor de símbolo. Ele fornece acesso direto aos metadados e `CorSym` interfaces.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll