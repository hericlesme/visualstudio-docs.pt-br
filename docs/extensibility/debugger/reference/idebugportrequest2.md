---
title: IDebugPortRequest2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2
helpviewer_keywords: IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f494eb3a48818323eedcb958a4126857b8d7ef5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Essa interface descreve uma porta. Essa descrição é usada para adicionar a porta para um fornecedor de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface no processo de obtenção de uma porta de depuração de um fornecedor de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é passada para [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para criar uma porta de depuração. Uma chamada para [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retorna essa interface, que representa a solicitação usada para criar a porta em primeiro lugar.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPortRequest2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtém o nome da porta para criar.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um mecanismo de depuração não consegue interagir com um fornecedor de porta e não terá nenhum uso para esta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)