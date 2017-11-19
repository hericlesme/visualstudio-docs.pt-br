---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94ca67611d77ae7da5f2e3fa1a6e0745871d8e1c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Recupera os filhos do símbolo que são válidos em um endereço virtual especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `symtag`  
 [in] Especifica as marcas de símbolo de filhos a serem recuperados, conforme definido no [SymTagEnum enumeração](../../debugger/debug-interface-access/symtagenum.md). Definido como `SymTagNull` para todos os filhos a serem recuperados.  
  
 `name`  
 [in] Especifica o nome dos filhos a serem recuperados. Definido como `NULL` para todos os filhos a serem recuperados.  
  
 `compareFlags`  
 [in] Especifica as opções de comparação a ser aplicado a correspondência de nomes. Os valores do [enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada sozinha ou em combinação.  
  
 `address`  
 [in] Especifica o endereço virtual.  
  
 `ppResult`  
 [out] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperado do objeto que contém uma lista dos símbolos filho.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se pelo menos um filho do símbolo foi encontrado ou retorna `S_FALSE` se nenhum filho foi encontrado; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os símbolos locais que são retornados incluem informações sobre o intervalo de tempo real.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)