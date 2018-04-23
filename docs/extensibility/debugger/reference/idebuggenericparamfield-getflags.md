---
title: IDebugGenericParamField::GetFlags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abeb26d0e8078eeaaf6ba6c8850b3636367bebc7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
Recupera os sinalizadores para esse parâmetro genérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```csharp  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 [out] Retorna os sinalizadores para esse parâmetro genérico.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esses sinalizadores contêm informações sobre várias restrições especiais.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugGenericParamFieldType** objeto que expõe o [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) interface.  
  
```cpp  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)