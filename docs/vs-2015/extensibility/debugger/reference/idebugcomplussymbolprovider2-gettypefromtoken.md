---
title: IDebugComPlusSymbolProvider2::GetTypeFromToken | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e46905b5ba7ab43f67ea6f46eb3172f1d40dadac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464317"
---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugComPlusSymbolProvider2::GetTypeFromToken](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken).  
  
Recupera um tipo de dado seu token.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetTypeFromToken(  
   ULONG32       appDomain,  
   GUID          guidModule,  
   DWORD         tdToken,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeFromToken(  
   uint            appDomain,  
   Guid            guidModule,  
   uint            tdToken,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `appDomain`  
 [in] Identificador do domínio do aplicativo.  
  
 `guidModule`  
 [in] Identificador exclusivo do módulo.  
  
 `tdToken`  
 [in] Token do tipo a ser recuperado.  
  
 `ppField`  
 [out] Retorna o tipo que é representado pela [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugSymbolProvider** objeto que expõe a [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypeFromToken(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    DWORD tdToken,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)

