---
title: 'Idiadatasource:: Opensession | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e4b0e1a1b105f349daed2fea03a290522f3ccb7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474481"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiadatasource:: Opensession](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiadatasource-opensession).  
  
Abre uma sessão para consultar os símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ppSession  
 [out] Retorna um [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto que representa a sessão aberta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores retornados para esse método.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_UNEXPECTED|O [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) objeto anteriormente não foi inicializado com uma origem de símbolos.|  
|E_INVALIDARG|Inválido `ppSession` parâmetro.|  
|E_OUTOFMEMORY|Memória insuficiente para abrir a sessão.|  
  
## <a name="remarks"></a>Comentários  
 Este método abre uma [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto para uma fonte de dados.  
  
 `IDiaSession` objetos de implementação de consultas na fonte de dados. Uma sessão gerencia um espaço de endereço para cada conjunto de símbolos de depuração. Se o arquivo. dll ou. .exe descrito pelos símbolos de fonte de dados estiver ativo no endereço vários intervalos (por exemplo, porque vários processos tem carregado) e uma sessão para cada intervalo de endereços deve ser usada.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Visão geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



