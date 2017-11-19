---
title: IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f465a4089d2d0503c953c39e914d1d15ceff0e0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Retorna uma enumeração de símbolos para os quadros entre linhas que correspondem ao local de origem especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `parent`  
 [in] Um `IDiaSymbol` que corresponde à função de stub de aceleração que precisa ser pesquisada.  
  
 `file`  
 [in] O `IDiaSourceFile` do local de origem.  
  
 `linenum`  
 [in] O número da linha do local de origem.  
  
 `colnum`  
 [in] O número da coluna do local de origem.  
  
 `ppResult`  
 [out] Um ponteiro para um `IDiaEnumLineNumbers` ponteiro de interface que é inicializado com o resultado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)