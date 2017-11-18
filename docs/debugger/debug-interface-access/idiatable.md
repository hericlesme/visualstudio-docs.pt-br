---
title: IDiaTable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be24edc89328f08199316df8bdedf2ab6391907b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiatable"></a>IDiaTable
Enumera uma tabela de fonte de dados do DIA.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDiaTable`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera o [IEnumVARIANT Interface](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versão este enumerador.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera o nome da tabela.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera o número de itens na tabela.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera uma referência a um índice de entrada específica.|  
  
## <a name="remarks"></a>Comentários  
 Implementa essa interface de `IEnumUnknown` métodos de enumeração no namespace Microsoft.VisualStudio.OLE.Interop. O `IEnumUnknown` interface de enumeração é muito mais eficiente para iteração sobre o conteúdo da tabela que o [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md) e [Idiatable](../../debugger/debug-interface-access/idiatable-item.md) métodos.  
  
 A interpretação de `IUnknown` interface retornou do `IDiaTable::Item` método ou o `Next` método (no namespace Microsoft.VisualStudio.OLE.Interop) é dependente do tipo de tabela. Por exemplo, se o `IDiaTable` interface representa uma lista de fontes injetados, o `IUnknown` interface deve ser consultada para o [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obter essa interface chamando o [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-item.md) ou [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-next.md) métodos.  
  
 As seguintes interfaces são implementadas com o `IDiaTable` interface (ou seja, você pode consultar o `IDiaTable` interface para uma das seguintes interfaces):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Exemplo  
 A primeira função, `ShowTableNames`, exibe os nomes de todas as tabelas na sessão. A segunda função, `GetTable`, procura todas as tabelas para uma tabela que implementa uma interface especificada. A terceira função, `UseTable`, mostra como usar o `GetTable` função.  
  
> [!NOTE]
>  `CDiaBSTR`é uma classe que encapsula um `BSTR` e manipula automaticamente libera a cadeia de caracteres quando a instanciação sai do escopo.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )  
            && celt == 1 )  
    {  
        CDiaBSTR bstrTableName;  
        if ( pTable->get_name( &bstrTableName ) != 0 )  
        {  
            Fatal( "get_name" );  
        }  
        printf( "Found table: %ws\n", bstrTableName );  
    }  
  
// Searches the list of all tables for a table that supports  
// the specified interface.  Use this function to obtain an  
// enumeration interface.  
HRESULT GetTable(IDiaSession* pSession,  
                 REFIID       iid,  
                 void**       ppUnk)  
{  
    CComPtr<IDiaEnumTables> pEnumTables;  
    HRESULT hResult;  
  
    if (FAILED(pSession->getEnumTables(&pEnumTables)))  
        Fatal("getEnumTables");  
  
    CComPtr<IDiaTable> pTable;  
    ULONG celt = 0;  
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&  
           celt == 1)  
    {  
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)  
        {  
            return S_OK;  
        }  
        pTable = NULL;  
    }  
  
    if (FAILED(hResult))  
        Fatal("EnumTables->Next");  
  
    return E_FAIL;  
}  
  
// This function shows how to use the GetTable function.  
void UseTable(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pEnumSegments;  
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))  
    {  
        // Do something with pEnumSegments.  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)