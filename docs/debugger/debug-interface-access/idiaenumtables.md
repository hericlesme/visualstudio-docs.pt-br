---
title: IDiaEnumTables | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913fdcefc4e90ea09030e416cb6a300e50855478
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Enumera as várias tabelas contidas na fonte de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDiaEnumTables`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Recupera o [IEnumVARIANT Interface](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versão este enumerador.|  
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Recupera o número de tabelas.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera uma tabela por meio de um índice ou um nome.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Recupera um número especificado de tabelas na sequência de enumeração.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignora um número especificado de tabelas em uma sequência de enumeração.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obter essa interface chamando o [: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) método.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como obter o `IDiaEnumTables` interface de uma sessão. Para obter um exemplo mais completo de como usar tabelas, consulte o [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface.  
  
```C++  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)