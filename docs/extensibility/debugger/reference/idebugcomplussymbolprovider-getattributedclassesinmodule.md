---
title: IDebugComPlusSymbolProvider::GetAttributedClassesinModule | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAttributedClassesinModule
- GetAttributedClassesinModule
ms.assetid: d8b087f3-1d32-4570-9eb0-7e0f7b051bc8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0784887b769ccb70ef323376cb3200f575fb807c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcomplussymbolprovidergetattributedclassesinmodule"></a>IDebugComPlusSymbolProvider::GetAttributedClassesinModule
Recupera as classes com o atributo especificado em um determinado módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[C++]  
HRESULT GetAttributedClassesinModule (  
   ULONG32            ulAppDomainID,  
   GUID               guidModule,  
   LPOLESTR           pstrAttribute,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```  
[C#]  
int GetAttributedClassesinModule (  
   uint                 ulAppDomainID,  
   Guid                 guidModule,  
   string               pstrAttribute,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ulAppDomainID`  
 [in] Identificador do domínio do aplicativo.  
  
 `guidModule`  
 [in] Identificador exclusivo do módulo.  
  
 `pstrAttribute`  
 [in] A cadeia de caracteres do atributo.  
  
 `ppEnum`  
 [out] Retorna uma enumeração das classes de atributo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CDebugSymbolProvider** objeto que expõe o [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetAttributedClassesinModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    __in_z LPOLESTR pstrAttribute,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    CComPtr<IMetaDataImport> pMetaData;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    const void* pUnused;  
    ULONG cbUnused;  
    HCORENUM hEnum = 0;  
    ULONG cTypeDefs = 0;  
    ULONG cEnum;  
    DWORD iTypeDef = 0;  
    mdTypeDef* rgTypeDefs = NULL;  
    IDebugField** rgFields = NULL;  
    DWORD ctField = 0;  
    CEnumDebugFields* pEnumFields = NULL;  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesinModule );  
  
    IfFalseGo( pstrAttribute && ppEnum , E_INVALIDARG );  
    IfFailGo( GetModule( idModule, &pModule ) );  
    pModule->GetMetaData( &pMetaData );  
  
    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                       NULL,  
                                       0,  
                                       &cTypeDefs ) );  
  
    IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
    pMetaData->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    IfNullGo( rgTypeDefs = new mdTypeDef[cEnum], E_OUTOFMEMORY );  
    IfNullGo( rgFields = new IDebugField * [cEnum], E_OUTOFMEMORY );  
  
    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                       rgTypeDefs,  
                                       cEnum,  
                                       &cTypeDefs ) );  
  
    for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)  
    {  
  
        if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],  
                pstrAttribute,  
                &pUnused,  
                &cbUnused ) == S_OK)  
        {  
            if (CreateClassType( idModule, rgTypeDefs[iTypeDef], rgFields + ctField) == S_OK)  
            {  
                ctField++;  
            }  
            else  
            {  
                ASSERT(!"Failed to Create Attributed Class");  
            }  
        }  
    }  
  
    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );  
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );  
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),  
                                           (void**) ppEnum ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesinModule, hr );  
  
    DELETERG( rgTypeDefs );  
  
    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)  
    {  
        RELEASE( rgFields[iTypeDef] );  
    }  
  
    DELETERG( rgFields );  
    RELEASE( pEnumFields );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)