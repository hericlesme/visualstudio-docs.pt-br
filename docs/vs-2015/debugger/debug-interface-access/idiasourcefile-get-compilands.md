---
title: 'Idiasourcefile:: Get_compilands | Microsoft Docs'
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
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc576a2fdd3b2a02b1b049a90bdf9f45f490f737
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473272"
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasourcefile:: Get_compilands](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-compilands).  
  
Recupera um enumerador de compilandos que têm números de linha, fazendo referência a esse arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppRetVal`  
 [out] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) objeto que contém uma lista de compilandos todos os que têm números de linha, fazendo referência a esse arquivo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



