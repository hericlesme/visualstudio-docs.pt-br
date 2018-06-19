---
title: ': Get_relativevirtualaddressenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25159556d44ca37d7938e67e67f1b9900a05010b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458015"
---
# <a name="idiaaddressmapgetrelativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Indica se o cálculo e o uso de endereços virtuais relativos (RVA) está habilitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pRetVal  
 [out] Retorna `TRUE` se o cálculo de RVAs está habilitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 RVAs estão habilitados se os segmentos foi inicialmente carregados de um arquivo PDB. O uso de RVAs pode ser desabilitado temporariamente chamando o [: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) método.  
  
 Além disso, novos cabeçalhos de imagem podem ser estabelecidos chamando o [: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método seguido por uma chamada para o `put_relativeVirtualAddressEnabled` método para habilitar o uso dos RVAs usando novos cabeçalhos de imagem.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)