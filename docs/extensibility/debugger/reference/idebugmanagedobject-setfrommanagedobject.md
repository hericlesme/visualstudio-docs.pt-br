---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da0526c060175a6e00a7b45a7ef2e347dba0d89e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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