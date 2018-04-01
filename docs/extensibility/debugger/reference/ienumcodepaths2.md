---
title: IEnumCodePaths2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f3da3fbbc8b7ad7dced8a9767b26859cc1a0de1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Essa interface representa uma lista de caminhos de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de caminhos de código.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumCodePaths2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera um número especificado de caminhos de código em uma sequência de enumeração.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignora um número especificado de caminhos de código em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtém o número de caminhos de código em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Um caminho de código representa uma ramificação ponto ou chamada de função em um programa. Uma lista de caminhos de código representa o caminho por meio do qual a execução de código tenha feito.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)