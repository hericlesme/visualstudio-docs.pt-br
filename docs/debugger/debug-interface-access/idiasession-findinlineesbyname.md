---
title: IDiaSession::findInlineesByName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0162e15d1692aa1ad6efef6a1a4d2a2088e8661
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
Recupera uma enumeração que permite que um cliente iterar por meio das informações de número de linha de todas as funções embutidas que corresponde a um nome especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 [in] Especifica o nome a ser usado para comparação.  
  
 `option`  
 [in] Especifica as opções de comparação aplicadas à pesquisa de nome. Os valores do [enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada sozinha ou em combinação.  
  
 `ppResult`  
 [out] Retorna um [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objeto que contém uma lista dos números de linha que foram recuperados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)