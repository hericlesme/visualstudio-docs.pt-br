---
title: IDebugModule3::LoadSymbols | Microsoft Docs
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
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f88ff4356b4292cf5b0bec3f066497a7a314b117
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472951"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugModule3::LoadSymbols](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule3-loadsymbols).  
  
Carrega os símbolos do módulo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, ele retornará `S_OK`. Se ele falhar, ele retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método carrega os símbolos do caminho de pesquisa atual (que pode ser alterado por meio da chamada a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) método).  
  
 Esse método é preferível a [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

