---
title: ': Symbolbyid | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70139b7bf3286e7c4527bd71cf78b4ba86aeac1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Recupera um símbolo por seu identificador exclusivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 [in] Identificador exclusivo.  
  
 `ppSymbol`  
 [out] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperado do objeto que representa o símbolo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O identificador especificado é um valor exclusivo usado internamente pelo DIA SDK para tornar exclusiva a todos os símbolos.  
  
 Esse método pode ser usado, por exemplo, para recuperar o símbolo que representa o tipo de outro símbolo (veja o exemplo).  
  
## <a name="example"></a>Exemplo  
 Este exemplo recupera uma [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o tipo de símbolo de outro. Este exemplo mostra como usar o `symbolById` método na sessão. Uma abordagem mais simples é chamar o [: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) método para recuperar o símbolo de tipo diretamente.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)