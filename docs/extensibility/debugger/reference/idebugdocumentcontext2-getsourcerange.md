---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::GetSourceRange
helpviewer_keywords: IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fc08e761b3944aafd2303bd7266c98dc06e1be8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Obtém o intervalo de código de origem deste contexto do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBegPosition`  
 [out no] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que é preenchida com a posição inicial. Defina este argumento como um valor nulo se essas informações não são necessárias.  
  
 `pEndPosition`  
 [out no] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que é preenchida com a posição final. Defina este argumento como um valor nulo se essas informações não são necessárias.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um intervalo de origem é o intervalo inteiro do código-fonte, na parte de trás instrução atual apenas após a instrução anterior que contribuiu com código. O intervalo de origem é normalmente usado para a combinação de instruções de origem, incluindo comentários, com o código na janela de desmontagem.  
  
 Para obter o intervalo para apenas as instruções de código contidas neste contexto de documento, chame o [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)