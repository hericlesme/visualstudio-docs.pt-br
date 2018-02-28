---
title: Interface IActiveScriptDebug | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>Interface IActiveScriptDebug
Implementado por mecanismos de script que suporte a depuração. Normalmente, um objeto que implementa o `IActiveScriptDebug` interface também implementa o `IActiveScript` interface. Se esse for o caso, chame o `IActiveScript::QueryInterface` método para obter o `IActiveScriptDebug` interface.  
  
 O `IActiveScriptDebug` interface fornece os meios para:  
  
-   Hosts inteligentes para assumir o gerenciamento de documentos.  
  
-   Gerenciador de depuração do processo para sincronizar a depuração de vários mecanismos de script.  
  
 Além dos métodos herdados de `IUnknown`, o `IActiveScriptDebug` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Retorna os atributos de texto de um bloco arbitrário de texto de script.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Retorna os atributos de texto para um miniscript arbitrário.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delega para `IDebugDocumentContext::EnumCodeContexts`.|