---
title: IDebugThread2::GetThreadProperties | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetThreadProperties
helpviewer_keywords: IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c118d8ccb4520cd63e2da91f0f807c7d6bc6ca8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Obtém as propriedades que descrevem esse thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadProperties (   
   THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES*     ptp  
);  
```  
  
```csharp  
int GetThreadProperties (   
   enum_THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES[]         ptp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumeração que determina quais campos de `ptp` devem ser preenchidos.  
  
 `ptp`  
 [out no] Um [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura que é preenchido com as propriedades do thread.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As informações retornadas deste método é geralmente mostradas no **Threads** janela de depuração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto que implementa o [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interface.  
  
```cpp  
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,  
                                      THREADPROPERTIES *ptp)  
{  
    HRESULT hr = E_FAIL;    
  
    // Check for valid argument.    
   if (ptp)    
    {    
      // Create an array of buffers at ptp the size of the  
      // THREADPROPERTIES structure and set all of the  
      // buffers at ptp to 0.    
      memset(ptp, 0, sizeof (THREADPROPERTIES));    
  
      // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.    
      if (dwFields & TPF_ID)    
      {    
         // Check for successful assignment of the current thread ID to  
         //  the dwThreadId of the passed THREADPROPERTIES.    
         if (GetThreadId(&(ptp->dwThreadId)) == S_OK)    
         {    
            // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator    
            // of the passed THREADPROPERTIES.    
            ptp->dwFields |= TPF_ID;    
         }    
      }    
  
      hr = S_OK;    
    }    
    else    
        hr = E_INVALIDARG;    
  
    return hr;    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)