---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5d294e401af09ec3c10fa6dabbb878c661b559e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Esse método obtém um objeto de propriedade que contém os locais, argumentos e outras propriedades de um método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSymbolProvider`  
 [in] O provedor de símbolo a ser usado, expresso como um [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.  
  
 `pAddress`  
 [in] O endereço no código, expressado como um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) função do objeto, que deve ser resolvido para o mais próximo que contém.  
  
 `pBinder`  
 [in] O associador a ser usada, expressa como um [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.  
  
 `fIncludeHiddenLocals`  
 [in] Diferente de zero (`TRUE`) inclui locais ocultos; zero (`FALSE`) significa que para omitir ocultas locais  
  
 `ppProperty`  
 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa o método.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Ocultas locais normalmente são variáveis que são gerados pelo compilador.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)