---
title: IDebugContainerField | Microsoft Docs
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
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a911fe64f397a3a671787db00877a07f5ed1ccaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464999"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugContainerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield).  
  
Essa interface representa um símbolo ou um tipo que é um contêiner para outros símbolos ou tipos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Essa interface também é a classe base para todas as interfaces que representam contêineres.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Muitos métodos em interfaces muitos retornam essa interface. Como esta é uma classe base para todos os contêineres, as interfaces mais especializadas podem ser obtidos usando dessa interface [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Essas interfaces incluem [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Cria um enumerador para os campos do contêiner.|  
  
## <a name="remarks"></a>Comentários  
 Matrizes (contêineres para variáveis), (contêineres para métodos e variáveis) de classes e métodos (contêineres para parâmetros e variáveis locais) são exemplos de contêineres.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

