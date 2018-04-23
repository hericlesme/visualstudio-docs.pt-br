---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7c4a09af356951e7e26b6c9b6b0af5922b9f53b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina se uma interface específica é definida na classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszInterfaceName`  
 [in] Uma cadeia de caracteres que contém o nome da interface a ser pesquisada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK, retornará S_FALSE se a interface não existe; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método em vigor obtém uma enumeração de todas as interfaces e as pesquisas a lista para a interface correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)