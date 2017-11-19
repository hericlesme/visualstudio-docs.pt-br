---
title: IDiaLoadCallback2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 474b6efeecc13b197f3189804682265beeba907e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Receber retornos de chamada do símbolo DIA localizar o procedimento, permitindo que restrições para imposto sobre o processo de localização.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos no [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interface, essa interface expõe os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina se a busca de um arquivo. PDB no diretório de depuração do original.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Determina se procurar por um arquivo. PDB é permitido no caminho de onde se encontra o arquivo .exe.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina se procurando por informações de depuração é permitida de arquivos. dbg.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina se procurar por arquivos. PDB é permitido no diretório raiz do sistema.|  
  
## <a name="remarks"></a>Comentários  
 O aplicativo cliente implementa essa interface e fornece uma referência a ele na chamada para o [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método. Lembre-se implementar todos os métodos no [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interface também.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)