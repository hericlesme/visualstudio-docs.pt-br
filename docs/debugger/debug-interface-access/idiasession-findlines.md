---
title: ': Findlines | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 366c41ee6befafa633428e2b6a959809a08b6cd9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Recupera os números de linha dentro de compiland especificado e identificadores de arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `compiland`  
 [in] Um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o compiland. Use esta interface como um contexto no qual pesquisar os números de linha.  
  
 `file`  
 [in] Um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto que representa o arquivo de origem no qual pesquisar os números de linha.  
  
 `ppResult`  
 [out] Retorna um [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) recuperado do objeto que contém uma lista de números de linha.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)