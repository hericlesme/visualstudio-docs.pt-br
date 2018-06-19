---
title: IDebugObject::GetValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50f65cba807abf4e8a0d7bc85ed28c765f7c6849
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112510"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtém o valor do objeto consecutivos de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pValue`  
 [out no] Uma matriz que é preenchida com consecutivos de bytes que representa o valor do objeto.  
  
 `nSize`  
 [in] O número máximo de bytes de busca.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Obter o número total de bytes do valor que pode ser obtido chamando o [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)