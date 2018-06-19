---
title: ': Put_addressmapenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb640a46825d720c5305a408fa716c6e3bed66c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465831"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Especifica se o mapa de endereço deve ser usado para converter os endereços de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 NewVal  
 [in] Definido como `TRUE` para habilitar a conversão de símbolos, ou `FALSE` para desabilitar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Pós-processadores de executável, às vezes, atualize o executável. DIA contém um mecanismo para oferecer suporte a tradução de símbolos para o novo layout.  
  
 Quando um arquivo PDB é carregado, armazenado no arquivo de mapa de endereço está habilitado. Há ocasiões, entretanto, quando um aplicativo cliente precisará fornecer seu próprio mapa de endereço chamando o [: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método. Se o `set_addressMap` método for bem-sucedido, o aplicativo cliente deve chamar o `put_addressMapEnabled` método com um `NewVal` parâmetro `TRUE` para permitir o uso do mapa de endereço.  
  
 O estado atual do mapa de endereço está sendo habilitado pode ser recuperado com uma chamada para o [: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)