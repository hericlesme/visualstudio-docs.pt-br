---
title: IDiaAddressMap | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0bff2d084abc51f22bccc8aeef42d1545a5ac9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Fornece controle sobre como o DIA SDK calcula endereços virtuais virtuais e relativos para objetos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDiaAddressMap`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica se um mapa de endereço foi estabelecido para uma determinada sessão.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Especifica se o mapa de endereço deve ser usado para converter os endereços de símbolo.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica se o cálculo e o uso de endereços virtuais relativos está habilitada.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permite que o cliente habilitar ou desabilitar o cálculo de endereços virtuais relativos.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera o alinhamento da imagem atual.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Define o alinhamento da imagem.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Conjuntos de cabeçalhos para habilitar a conversão de endereços virtuais relativos da imagem.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fornece um mapa de endereço para dar suporte a conversões de layout de imagem.|  
  
## <a name="remarks"></a>Comentários  
 O controle fornecido por esta interface é encapsulado em dois conjuntos de dados que você fornecer: cabeçalhos de imagens e mapas de endereço. A maioria dos clientes usam o [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método para encontrar as informações de depuração apropriado para uma imagem e o método normalmente podem descobrir todos os dados necessários de cabeçalhos e mapas em si. No entanto, alguns clientes implementam especializada de processamento e a pesquisa de dados. Esses clientes usam os métodos do `IDiaAddressMap` interface para fornecer o DIA SDK com os resultados da pesquisa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface está disponível no objeto de sessão DIA. O cliente chama o `QueryInterface` método no DIA sessão interface de objeto, normalmente [IDiaSession](../../debugger/debug-interface-access/idiasession.md)para recuperar o `IDiaAddressMap` interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)