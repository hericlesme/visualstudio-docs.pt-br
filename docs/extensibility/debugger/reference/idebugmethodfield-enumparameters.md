---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f60fbde074f660647aedd65a7bae7f98576d485d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Cria um enumerador para os parâmetros do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de parâmetros para o método do objeto; caso contrário, retornará um valor nulo se não houver nenhum parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver nenhum parâmetro. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento é um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto representando diferentes tipos de parâmetros. Chamar o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em cada objeto para determinar exatamente quais tipos de parâmetro que o objeto representa.  
  
 Um parâmetro inclui o nome da variável e seu tipo. O primeiro parâmetro para um método de classe normalmente é o ponteiro "this".  
  
 Se apenas os tipos dos parâmetros for necessário, chame o [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)