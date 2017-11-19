---
title: Idiaenumsourcefiles | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 778152f721222efab46f0bf10a53f808abe4be3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Clone (   
   IDiaEnumSourceFiles** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ppenum  
 [out] Retorna um [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) objeto que contém uma duplicata do enumerador. A fonte de arquivos não são duplicadas, apenas o enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)