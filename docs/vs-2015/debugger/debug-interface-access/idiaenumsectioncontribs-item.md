---
title: 'Idiaenumsectioncontribs:: item | Microsoft Docs'
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
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7d1c8f3e2832dbe4b2fd270bea4c65c00d45222
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472935"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiaenumsectioncontribs:: item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsectioncontribs-item).  
  
Recupera as contribuições de seção por meio de um índice.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 índice  
 [in] Índice do [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) objeto a ser recuperado. O índice está no intervalo de 0 a `count`-1, onde `count` é retornado pelo [idiaenumsectioncontribs:: Get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) método.  
  
 section  
 [out] Retorna um [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) objeto que representa a contribuição da seção desejado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [Idiaenumsectioncontribs:: Get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



