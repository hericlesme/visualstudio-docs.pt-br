---
title: IDebugMethodField::EnumParameters | Microsoft Docs
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
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51e51a3c8dffebb90b36f60df6859d1cfdf4db6f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467661"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugMethodField::EnumParameters](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield-enumparameters).  
  
Cria um enumerador para os parâmetros do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppParams`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de parâmetros para o método; caso contrário, retornará um valor nulo se não houver nenhum parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum parâmetro. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento é um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa os diferentes tipos de parâmetros. Chame o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em cada objeto para determinar exatamente quais tipos de parâmetro que o objeto representa.  
  
 Um parâmetro inclui seu nome de variável e seu tipo. O primeiro parâmetro para um método de classe normalmente é o ponteiro "this".  
  
 Se apenas os tipos dos parâmetros for necessário, chame o [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

