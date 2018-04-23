---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84ac767c8e2cd53045dec9921f6d90300f1a87e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Recupera o nome do contexto de avaliação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrName`  
 [out] Retorna o nome do contexto de avaliação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O nome é a descrição deste contexto de avaliação. Geralmente, é algo que podem ser analisados por um avaliador de expressão que faz referência a este contexto de avaliação exato. Por exemplo, em C++ o nome é da seguinte maneira:  
  
```  
"{ function-name, source-file-name, module-file-name }"  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)