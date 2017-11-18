---
title: ': Get_checksumtype | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fafd9e813c22b899603a2e62c5a2c90ece1a709
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Recupera o tipo de soma de verificação.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o tipo de soma de verificação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O tipo de soma de verificação é um valor que pode ser mapeado para um algoritmo de soma de verificação. Por exemplo, o formato de arquivo PDB padrão normalmente pode ter um dos seguintes valores:  
  
|Tipo de soma de verificação|Rótulo de CryptoAPI|Descrição|  
|-------------------|---------------------|-----------------|  
|0|\<Nenhum >|Nenhuma soma de verificação presente.|  
|1|`CALG_MD5`|soma de verificação gerada com o algoritmo de hash MD5.|  
|2|`CALG_SHA1`|soma de verificação gerada com o algoritmo de hash SHA1.|  
  
 O `CryptoAPI` são rótulos do `ALG_ID` enumeração. Para obter mais informações sobre algoritmos de hash, consulte o `CryptoAPI` seção do Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Para obter os bytes reais de soma de verificação para o arquivo de origem, chame o [: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)