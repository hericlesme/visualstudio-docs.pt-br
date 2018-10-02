---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
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
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bba4ac471968a720632279bd5c20d1b53b8b5e5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467733"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPropertyCreateEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpropertycreateevent2).  
  
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando ele cria uma propriedade que está associada um documento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para relatar que uma propriedade foi criada. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface. Usa o SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar o `IDebugEvent2` interface. Essa interface é implementada, se o DE tiver criado uma propriedade associada a um script que foi carregado ou criado e se esse script precisa aparecer no IDE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para relatório de que uma propriedade foi criada. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra o método da `IDebugPropertyCreateEvent2` interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtém a nova propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Se uma propriedade tiver um documento específico ou o script associado a ele, o DE pode enviar esse evento para o SDM para atualizar o **documentos de Script** janela com o nome do documento. O SDM chamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) com o argumento `guidDocument` para recuperar um `VARIANT` que contém um [IUnknown](http://msdn.microsoft.com/library/e6b85472-e54b-4b8c-b19f-4454d6c05a8f) ponteiro. O SDM chamará [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nesse ponteiro para recuperar o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface que é usado para atualizar o **documentos de Script** janela.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

