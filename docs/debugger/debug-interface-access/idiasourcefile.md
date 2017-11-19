---
title: IDiaSourceFile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b742986d59024021eff5e85d54fc64247571df61
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Representa um arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDiaSourceFile`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Recupera um valor de chave inteiro simples que é exclusivo para esta imagem.|  
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Recupera o nome do arquivo de origem.|  
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Recupera o tipo de soma de verificação.|  
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Recupera um enumerador dos compilandos com números de linha referenciar este arquivo.|  
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Recupera os bytes de soma de verificação.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obter essa interface chamando o [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) ou [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) métodos. Consulte o exemplo para obter detalhes.  
  
## <a name="example"></a>Exemplo  
 Esta função exibe os nomes de todos os arquivos de origem que contribuem para a tabela especificada.  
  
```C++  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [Idiaenumsourcefiles](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [: Get_sourcefile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [: Findfilebyid](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)