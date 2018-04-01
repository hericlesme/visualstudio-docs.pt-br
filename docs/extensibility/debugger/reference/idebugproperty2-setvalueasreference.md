---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7bd9e42ae6be1cbd5afe1cbe2ae1b06da7f9937f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Define o valor dessa propriedade para o valor da referência fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rgpArgs`  
 [in] Uma matriz de argumentos para passar para o setter de propriedade de código gerenciado. Se a propriedade setter não obtém argumentos ou se esse [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto não faz referência a esse um setter de propriedade `rgpArgs` deve ser um valor nulo. Normalmente, este parâmetro é um valor nulo.  
  
 `dwArgCount`  
 [in] O número de argumentos a `rgpArgs` matriz.  
  
 `pValue`  
 [in] Uma referência, na forma de um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto, o valor a ser usado para definir essa propriedade.  
  
 `dwTimeout`  
 [in] Quanto tempo deve demorar para definir o valor, em milissegundos. Um valor típico é `INFINITE`. Isso afeta o período de tempo que pode executar qualquer avaliação possível.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retornará um erro de código, normalmente um dos seguintes:  
  
|Erro|Descrição|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Não há suporte para a definição do valor de uma referência.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|O valor não pode ser definido como essa propriedade se refere a um método.|  
|`E_SETVALUE_VALUE_IS_READONLY`|O valor é somente leitura e não pode ser definido.|  
|`E_NOTIMPL`|O método não está implementado.|  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)