---
title: ': Get_imagebase | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cd7cb16a4f6a6a629102eafbc212e4b2fff0f00
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458675"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Recupera o local de memória em que a imagem deve ser baseada.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o valor de base de imagem sugeridas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Devido a conflitos de base de imagem, uma imagem pode ser restabelecida automaticamente em um local de memória não utilizada quando ele é carregado. Esse método retorna a dica de base (local de memória sugerido) que foi armazenada no módulo em tempo de compilação.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)