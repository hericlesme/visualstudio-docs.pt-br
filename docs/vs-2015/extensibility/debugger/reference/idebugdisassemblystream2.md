---
title: IDebugDisassemblyStream2 | Microsoft Docs
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
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f72cea28e47bdd14681c1f843a2620a43162885
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474451"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugDisassemblyStream2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2).  
  
Essa interface representa um fluxo de instruções.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um mecanismo de depuração implementa essa interface para dar suporte a desmontagem do código do programa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para o [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método retorna essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugDisassemblyStream2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Ler](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lê a partir da posição atual no fluxo de desmontagem de instruções.|  
|[Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Move o ponteiro de leitura no fluxo de desmontagem um determinado número de instruções em relação a uma posição especificada.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Retorna um identificador de local de código para um contexto de código em particular.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Retorna um objeto de contexto de código correspondente a um identificador de local de código especificada.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Retorna um identificador de local do código que representa o local atual do código.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtém o documento de origem associado a este fluxo de desmontagem.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtém o escopo deste fluxo de desmontagem.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtém o tamanho deste fluxo de desmontagem.|  
  
## <a name="remarks"></a>Comentários  
 O fluxo de desmontagem pode ser criado para representar o espaço de endereço inteiro ou apenas uma função ou módulo dentro do espaço. Cada instrução é representada por um [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura retornada por uma chamada para o [leitura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

