---
title: Idiastackwalkframe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d23b46f0f487bddc678814e41b5cb96331ff46c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463309"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lê a memória da imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
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
 [in] Uma da [enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) valores de enumeração que especifica o tipo de memória para acessar.  
  
 `va`  
 [in] Local de endereço virtual de imagem para iniciar a leitura.  
  
 `cbData`  
 [in] Tamanho do buffer de dados, em bytes.  
  
 `pcbData`  
 [out] Retorna o número de bytes retornados. Se `data` é `NULL`, em seguida, `pcbData` contém o número total de bytes de dados disponíveis.  
  
 `data`  
 [out] Um buffer é preenchido com dados do local especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)