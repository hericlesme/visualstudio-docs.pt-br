---
title: 'Idiaenumframedata:: Framebyva | Microsoft Docs'
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
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf9a56c335deee9accc203af70d16090813f1c70
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462927"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiaenumframedata:: Framebyva](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumframedata-framebyva).  
  
Retorna um quadro por endereço virtual (VA).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 virtualAddress  
 [in] VA do quadro de interesse.  
  
 moldura  
 [out] Retorna um [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa o quadro que contém o endereço fornecido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o endereço especificado não corresponde a nenhum dado de quadro. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



