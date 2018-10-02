---
title: 'Idiatable:: item | Microsoft Docs'
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
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ad4b51a125af1f08d8766c4c34a2bdd0c54ff64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475185"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiatable:: item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiatable-item).  
  
Recupera uma referência para a entrada especificada na tabela.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `index`  
 [in] O índice da entrada da tabela no intervalo de 0 a `count`-1, onde `count` é retornado pelo [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)método.  
  
 `element`  
 [out] Retorna um `IUnknown` objeto que representa a entrada da tabela especificada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma tabela representa uma coleção de objetos. Dependendo desses objetos, o parâmetro de elemento pode ser convertido para a interface apropriada. Por exemplo, se uma tabela contiver [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos, em seguida, o parâmetro de elemento pode ser convertido para o `IDiaSegment` interface.  
  
 É uma abordagem mais comum para chamar o `QueryInterface` método na [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface para a interface de enumerador apropriado e usar métodos de específicos do enumerador para acessar o conteúdo da tabela. Consulte a [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface para obter um exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



