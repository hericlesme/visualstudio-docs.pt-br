---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61cb7304f6fed3e2f3da55b94450c58bfc53334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109669"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtém os bytes de atributos personalizados, considerando o nome do atributo personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCustomAttributeName`  
 [in] Uma cadeia de caracteres que contém o nome do atributo personalizado a ser pesquisada.  
  
 `ppBlob`  
 [out no] Uma matriz que é preenchida com os bytes de atributo personalizado.  
  
 `pdwLen`  
 [out no] Especifica o número máximo de bytes a serem retornados no `ppBlob` de matriz e retorna o número de bytes gravados para a matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se o atributo personalizado não existe. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Definir o `ppBlob` atributos de parâmetro para um valor null para retornar o número de bytes disponíveis. Em seguida, aloque uma matriz e passar a matriz para o `ppBlob` parâmetro.  
  
 Os bytes de atributo representam os dados brutos do atributo personalizado.  
  
 Se o `ppBlob` e `pdwLen` parâmetros são definidos como um valor nulo, esse método pode ser usado para determinar se o atributo personalizado simplesmente existe. No entanto, é uma alternativa mais fácil chamar o [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)