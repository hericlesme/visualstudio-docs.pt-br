---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
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
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8ef913a94dc184339d6c20c97ca8c3f0f3054a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467009"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDiaStackWalkHelper::readMemory](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-readmemory).  
  
Lê um bloco de dados de imagem do arquivo executável na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 [in] Um valor da [enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) enumeração que especifica o tipo de memória a ser lido.  
  
 VA  
 [in] Endereço virtual na imagem a partir do qual será iniciada a leitura.  
  
 `cbData`  
 [in] O tamanho do buffer de dados em bytes.  
  
 `pcbData`  
 [out] Retorna o número de bytes realmente lidos. Se `pbData` é `NULL`, em seguida, isso é o número total de bytes de dados disponíveis.  
  
 `pbData`  
 [no, out] Um buffer que será preenchido com a memória de leitura.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)



