---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Microsoft Docs'
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
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8202cb3ad7449d282e449fcfd8b284987c8f390d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475016"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiareadexeatoffsetcallback:: Readexecutableat](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat).  
  
Lê o número especificado de bytes, começando no deslocamento especificado de um arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 fileOffset  
 [in] O deslocamento no arquivo executável para iniciar a leitura.  
  
 cbData  
 [in] Número de bytes a serem lidos.  
  
 pcbData  
 [out] Retorna o número de bytes lidos.  
  
 [Data]  
 [no, out] Uma matriz que é preenchida com bytes lidos do arquivo.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado pelo código de suporte do DIA para carregar os bytes de dados de um executável usando um deslocamento de arquivo absoluto. Esse método é chamado suportados a [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



