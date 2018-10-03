---
title: IDiaAddressMap | Microsoft Docs
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
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd3f624e7b6889b64d81e06792404ff20839b03e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466521"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDiaAddressMap](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap).  
  
Fornece controle sobre como o DIA SDK calcula relativos e virtuais endereços virtuais para objetos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaAddressMap`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica se um mapa de endereço foi estabelecido para uma determinada sessão.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Especifica se o mapa de endereço deve ser usado para converter endereços de símbolo.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se o cálculo e o uso de endereços virtuais está habilitado.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permite ao cliente habilitar ou desabilitar o cálculo de endereços virtuais.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera o alinhamento da imagem atual.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Define o alinhamento da imagem.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Conjuntos de imagem cabeçalhos para habilitar a conversão de endereços virtuais.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornece um mapa de endereço para dar suporte a traduções de layout da imagem.|  
  
## <a name="remarks"></a>Comentários  
 O controle fornecido por esta interface é encapsulado em dois conjuntos de dados que você forneça: cabeçalhos de imagem e mapas de endereço. A maioria dos clientes usam o [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método para localizar as informações de depuração adequado para uma imagem e o método normalmente podem descobrir todos os dados necessários para cabeçalhos e mapas em si. No entanto, alguns clientes implementam processamento especializados e a pesquisa de dados. Esses clientes usam os métodos do `IDiaAddressMap` interface para fornecer o DIA SDK com os resultados da pesquisa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Esta interface está disponível do objeto de sessão de DIA. O cliente chama o `QueryInterface` método no DIA sessão interface de objeto, normalmente [IDiaSession](../../debugger/debug-interface-access/idiasession.md), para recuperar o `IDiaAddressMap` interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



