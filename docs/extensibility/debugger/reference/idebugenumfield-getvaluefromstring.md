---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31e7985491833be8243a30bd3134db2d1af1d2cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Esse método retorna o valor associado com o nome de uma constante de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 [in] Uma cadeia de caracteres especificando o nome para o qual obter o valor. Observe que para C++, essa é uma cadeia de caracteres larga.  
  
 `pValue`  
 [out] Retorna o valor numérico associado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE`, se o nome não é parte de enumeração ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método diferencia maiusculas de minúsculas. Se for necessária uma pesquisa diferencia maiusculas de minúsculas (por exemplo, em uma linguagem, como Visual Basic, em que os nomes não diferenciam maiusculas de minúsculas), use [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)