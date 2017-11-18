---
title: ': Findfilebyid | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1996bed14323adeac794f12ed4307e96e3ba8b54
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Recupera um arquivo de origem pelo identificador de arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `uniqueId`  
 [in] Especifica o identificador de arquivo de origem.  
  
 `ppResult`  
 [out] Retorna um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) recuperado do objeto que representa o arquivo de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O identificador de arquivo de origem é um valor exclusivo usado internamente para o DIA SDK para tornar exclusiva a todos os arquivos de origem. Esse método normalmente é usada internamente para o DIA SDK.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)