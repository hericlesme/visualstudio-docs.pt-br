---
title: ': Readexecutableatrva | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 71dd19f15d631c58e99a826ab1ff274b993afd5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lê o número especificado de bytes, começando no relativo virtual endereço especificado (RVA) do arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `relativeVirtualAddress`  
 [in] RVA no arquivo executável para iniciar a leitura.  
  
 `cbData`  
 [in] Número de bytes a serem lidos.  
  
 `pcbData`  
 [out] Retorna o número de bytes lidos.  
  
 `data[]`  
 [out no] Uma matriz que é preenchida com bytes lidos do arquivo.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado pelo código de suporte do DIA para carregar os bytes de dados de um executável usando um endereço virtual relativo. Este método é chamado suportados de [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)