---
title: ': Notifydebugdir | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46621c667967f0b87d197839012e830207cc306a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Chamado quando um diretório de depuração foi encontrado no arquivo .exe.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fExecutable`  
 [in] `TRUE` se o diretório de depuração é lido de um arquivo executável (em vez de um arquivo. dbg).  
  
 `cbData`  
 [in] Contagem de bytes de dados no diretório de depuração.  
  
 `data[]`  
 [in] Uma matriz que é preenchida com o diretório de depuração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. O código de retorno normalmente é ignorado.  
  
## <a name="remarks"></a>Comentários  
 O [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método invoca esse retorno de chamada quando ele encontra um diretório de depuração ao processar o arquivo executável.  
  
 Este método remove a necessidade do cliente para o arquivo executável e/ou a depuração de engenharia reversa para dar suporte a informações de depuração que não seja encontrado no arquivo. PDB. Com esses dados, o cliente pode reconhecer o tipo de informações de depuração disponíveis e se ela reside no arquivo executável ou de arquivos. dbg.  
  
 A maioria dos clientes não precisará esse retorno de chamada porque o `IDiaDataSource::loadDataForExe` método transparentemente abre arquivos. PDB e. dbg quando necessário para atender os símbolos.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)