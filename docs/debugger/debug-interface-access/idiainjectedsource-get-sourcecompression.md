---
title: ': Get_sourcecompression | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbf917a219443051da95634e8dc3263b3927c719
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Recupera o indicador de origem de compactação de usado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o indicador de origem de compactação de usado. Um valor de zero indica que foi usada nenhuma compactação de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O valor retornado por esse método é específico para o compilador usado. Por exemplo, um compilador pode usar compactação Huffman-estilo ou codificação de comprimento de execução.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)