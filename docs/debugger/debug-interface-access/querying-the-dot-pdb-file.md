---
title: Consultando o. O arquivo PDB | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da12d0cde9e8dae0d291985bc8bf88931ab35ec5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-pdb-file"></a>Consultando o arquivo .Pdb
Um arquivo de banco de dados do programa (extensão. PDB) é um arquivo binário que contém o tipo e informações de depuração simbólicas coletadas durante o curso de compilar e vincular o projeto. Um arquivo PDB é criado quando você compila um programa C/C++ com **/ZI** ou **/Zi** ou um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] de programa com o **/Debug** opção. Arquivos de objeto contêm referências para o arquivo. PDB para informações de depuração. Para obter mais informações sobre arquivos pdb, consulte [arquivos PDB](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Um aplicativo de DIA pode usar as seguintes etapas gerais para obter detalhes sobre os vários símbolos, objetos e elementos de dados em uma imagem executável.  
  
### <a name="to-query-the-pdb-file"></a>Para consultar o arquivo. PDB  
  
1.  Adquirir uma fonte de dados, criando um [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interface.  
  
    ```C++  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  Chamar [: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) ou [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para carregar as informações de depuração.  
  
    ```C++  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  Chamar [: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) para abrir um [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para acessar as informações de depuração.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Use os métodos no `IDiaSession` para consultar os símbolos na fonte de dados.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Use o `IDiaEnum*` interfaces para enumerar e examinar os símbolos ou outros elementos de informações de depuração.  
  
    ```C++  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)