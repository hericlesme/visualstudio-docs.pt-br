---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d240c931db24cc353d7bb461645771eb4520921
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110888"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Define o valor da instância do objeto de classe de valor da instância da classe de valor fornecido como um parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pManagedObject`  
 [in] Uma interface que representa o objeto gerenciado que contém o novo valor.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado para alterar o objeto gerenciado conforme representado pelo [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)