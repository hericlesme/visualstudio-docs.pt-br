---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d240388ee1331e8dbdb2148f58f7a761ddde7a83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464498"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugDocumentPosition2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentposition2).  
  
Essa interface representa uma posição abstrata em um arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface. Um mecanismo de depuração (DES) também deve implementar essa interface se ele deve fornecer seu próprio código-fonte (como quando o DE implementa o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é passada como um argumento para [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Ele também é fornecido como parte de um [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) união (especificamente, um [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) estrutura) que por sua vez faz parte dos [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura, que é usado na criação de um ponto de interrupção pendente.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugDocumentPosition2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtém o nome do arquivo do arquivo de origem que contém essa posição do documento.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtém a que contém o documento.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se essa posição está contida em um determinado documento.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtém o intervalo para essa posição do documento.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)

