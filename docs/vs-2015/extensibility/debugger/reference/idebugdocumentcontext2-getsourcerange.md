---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
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
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73600b81c71a1337470a1975902c40292ab4dcef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467353"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugDocumentContext2::GetSourceRange](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange).  
  
Obtém o intervalo de código de origem deste contexto de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [no, out] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura será preenchida com a posição inicial. Defina este argumento como um valor nulo se essa informação não é necessária.  
  
 `pEndPosition`  
 [no, out] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura será preenchida com a posição final. Defina este argumento como um valor nulo se essa informação não é necessária.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um intervalo de origem é o intervalo inteiro de código-fonte, da parte traseira da instrução atual para somente após a instrução anterior que contribuíram de código. O intervalo de origem normalmente é usado para misturar as instruções de código-fonte, incluindo comentários, com o código na janela de desmontagem.  
  
 Para obter o intervalo para apenas as instruções de código contidas neste contexto de documento, chame o [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

