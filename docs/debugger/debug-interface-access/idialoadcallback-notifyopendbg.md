---
title: ': Notifyopendbg | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8454a795200c9e0aea850a2a75a25403d5c0c2c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
Chamado quando um arquivo. dbg candidato foi aberto.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dbgPath`  
 [in] O caminho completo do arquivo. dbg.  
  
 `resultCode`  
 [in] Código que indica o sucesso (`S_OK`) ou a falha da carga conforme aplicado a este arquivo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. O código de retorno normalmente é ignorado.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)