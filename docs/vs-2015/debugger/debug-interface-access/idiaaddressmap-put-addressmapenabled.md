---
title: 'Idiaaddressmap:: Put_addressmapenabled | Microsoft Docs'
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
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe8d1dcd58c745bdba44f1fa895ba87cb6a9b7f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474133"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiaaddressmap:: Put_addressmapenabled](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled).  
  
Especifica se o mapa de endereço deve ser usado para converter endereços de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 NewVal  
 [in] Definido como `TRUE` para habilitar a conversão de símbolos, ou `FALSE` para desabilitar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Pós-processadores de executáveis, às vezes, atualize o executável. DIA contém um mecanismo para dar suporte a tradução de símbolos para o novo layout.  
  
 Quando um arquivo PDB é carregado, armazenado no arquivo de mapa de endereço está habilitado. Há vezes, no entanto, quando um aplicativo cliente talvez seja necessário fornecer seu próprio mapa de endereço chamando o [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método. Se o `set_addressMap` método for bem-sucedido, o aplicativo cliente deve chamar o `put_addressMapEnabled` método com um `NewVal` parâmetro do `TRUE` para habilitar o uso desse mapa de endereço.  
  
 O estado atual do mapa de endereço que está sendo habilitado pode ser recuperado com uma chamada para o [idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)



