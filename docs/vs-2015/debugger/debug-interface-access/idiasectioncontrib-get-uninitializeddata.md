---
title: 'Idiasectioncontrib:: Get_uninitializeddata | Microsoft Docs'
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
- IDiaSectionContrib::get_uninitializedData method
ms.assetid: 39736f35-6c73-4f54-a092-517192e417ff
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adb77aca3ae33c17492a41f5adc49108d03fcd27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467695"
---
# <a name="idiasectioncontribgetuninitializeddata"></a>IDiaSectionContrib::get_uninitializedData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiasectioncontrib:: Get_uninitializeddata](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata).  
  
Recupera um sinalizador que indica se a seção contém dados não inicializados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_uninitializedData (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se a seção contém os dados não inicializado; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



