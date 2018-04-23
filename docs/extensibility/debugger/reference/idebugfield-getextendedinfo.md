---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63bf182e4e8b17133fbefd4f4a19c4b8b4a458e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Esse método obtém informações estendido sobre um campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidExtendedInfo`  
 [in] Seleciona as informações a serem retornadas. Os valores válidos são:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`guidConstantValue`|O valor como uma sequência de bytes.|  
|`guidConstantType`|O tipo como uma assinatura de tipo.|  
  
 `prgBuffer`  
 [out] Retorna as informações estendidas.  
  
 `pdwLen`  
 [out no] Retorna o tamanho das informações estendidas, em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Atualmente, esse método retorna apenas o tipo ou valor de uma constante. O chamador deve liberar o buffer retornado em `prgBuffer` chamando COM `CoTaskMemFree` função (C++) ou <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)