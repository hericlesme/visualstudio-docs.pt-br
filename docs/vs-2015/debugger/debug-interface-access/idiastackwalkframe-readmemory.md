---
title: 'Idiastackwalkframe:: Readmemory | Microsoft Docs'
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
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e4bad4128ca89cf90ccf1c361bcc6de11d1d8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466319"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [idiastackwalkframe:: Readmemory](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkframe-readmemory).  
  
Lê a memória da imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 [in] Um dos [enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) valores de enumeração que especifica o tipo de memória para acessar.  
  
 `va`  
 [in] Local de endereço virtual de imagem será iniciada a leitura.  
  
 `cbData`  
 [in] Tamanho do buffer de dados, em bytes.  
  
 `pcbData`  
 [out] Retorna o número de bytes retornados. Se `data` está `NULL`, em seguida, `pcbData` contém o número total de bytes de dados disponíveis.  
  
 `data`  
 [out] Um buffer que deve ser preenchido com dados do local especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



