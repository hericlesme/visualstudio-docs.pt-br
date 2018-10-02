---
title: 'Idialinenumber:: Get_compilandid | Microsoft Docs'
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
- IDiaLineNumber::get_compilandId method
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd050f440d745911e29781b2fbb23a20f8f05bc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472459"
---
# <a name="idialinenumbergetcompilandid"></a>IDiaLineNumber::get_compilandId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idialinenumber:: Get_compilandid](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialinenumber-get-compilandid).  
  
Recupera um identificador exclusivo para o compiland que contribuíram nesta linha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `DWORD` que contém o identificador exclusivo para o compiland que contribuíram nesta linha.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



