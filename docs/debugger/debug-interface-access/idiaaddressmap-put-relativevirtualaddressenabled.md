---
title: ': Put_relativevirtualaddressenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbbe2c2299a26834ac40c787aea5504ae7d0ed8a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31456562"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Permite que o cliente habilitar ou desabilitar o cálculo e o uso de endereços virtuais relativos (RVA).  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 NewVal  
 [in] Definido como `TRUE` para habilitar, ou `FALSE` para desabilitar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Endereços para depurar objetos descritos pelas interfaces do DIA e, em relação a base de imagem do executável podem ser recuperados como endereços virtuais relativos.  
  
 O uso de RVAs é habilitado quando segmentos são inicialmente carregados de um arquivo PDB. Para obter o estado atual do uso de RVAs, chame o [: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método.  
  
 O `put_relativeVirtualAddress` método deve ser chamado para habilitar RVAs após uma chamada bem-sucedida para o [: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método estabeleceu novos cabeçalhos de imagem.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)