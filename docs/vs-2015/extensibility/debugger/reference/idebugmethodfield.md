---
title: IDebugMethodField | Microsoft Docs
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
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09161f400b2917aeff4c79ba58a813a98e6b5f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468124"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugMethodField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield).  
  
Essa interface descreve um método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface. Essa interface é uma especialização que apresenta um método.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para obter essa interface da [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retorna `FIELD_TYPE_METHOD`. Além disso, os métodos [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), e [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), retornam o `IDebugMethodField` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Cria um enumerador para os parâmetros do método.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtém o ponteiro "this" do objeto que contém o método.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Cria um enumerador para todas as variáveis locais do método.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Cria um enumerador para variáveis locais selecionados do método.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Determina se um atributo personalizado específico foi definido.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Cria um enumerador para variáveis locais estáticas do método.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Obtém o contêiner global do método.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Cria um enumerador para o tipo de cada argumento necessário para chamar o método.|  
  
## <a name="remarks"></a>Comentários  
 Um método pode conter parâmetros, bem como as variáveis locais.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

