---
title: ': Set_imageheaders | Microsoft Docs'
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
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 74556e2e67478cef9b495d3740dc910b62cc8293
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Conjuntos de cabeçalhos para habilitar a conversão de endereço virtual relativo da imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 cbData  
 [in] Número de bytes de dados de cabeçalho. Deve ser `n*sizeof(IMAGE_SECTION_HEADER)` onde `n` é o número de cabeçalhos de seção no executável.  
  
 [Data]  
 [in] Uma matriz de `IMAGE_SECTION_HEADER` estruturas para ser usado como o cabeçalho de imagem.  
  
 originalHeaders  
 [in] Definido como `FALSE` se os cabeçalhos de imagem da nova imagem, `TRUE` se eles refletem a imagem original antes de uma atualização. Normalmente, isso deve ser definido como `TRUE` apenas em combinação com chamadas para o [: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `IMAGE_SECTION_HEADER` estrutura é declarada em Winnt. h e representa o formato de cabeçalho de seção de imagem do executável.  
  
 Cálculos de endereço virtual relativo dependem de `IMAGE_SECTION_HEADER` valores. Geralmente, o DIA recupera esses do arquivo de banco de dados (. PDB) do programa. Se esses valores estão ausentes, o DIA é não é possível calcular endereços virtuais relativos e o [: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método retornará `FALSE`. O cliente deve, em seguida, chamar o [: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) método para permitir que os cálculos de endereço virtual relativo depois de fornecer os cabeçalhos de imagem ausentes da imagem em si.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)