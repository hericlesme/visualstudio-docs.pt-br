---
title: Idiatable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c0c810dfd1a17f2fa63e64bf199a5882174aae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiatableitem"></a>IDiaTable::Item
Recupera uma referência para a entrada especificada na tabela.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `index`  
 [in] O índice da entrada de tabela no intervalo de 0 a `count`-1, onde `count` é retornado pelo [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)método.  
  
 `element`  
 [out] Retorna um `IUnknown` objeto que representa a entrada da tabela especificada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma tabela representa uma coleção de objetos. Esses objetos, dependendo do parâmetro de elemento pode ser convertido para a interface apropriada. Por exemplo, se uma tabela contiver [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos, em seguida, o parâmetro de elemento pode ser convertido para o `IDiaSegment` interface.  
  
 É uma abordagem mais comum para chamar o `QueryInterface` método o [IDiaTable](../../debugger/debug-interface-access/idiatable.md) a interface para a interface de enumerador apropriado e use métodos específicos do enumerador para acessar o conteúdo da tabela. Consulte o [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface para obter um exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)