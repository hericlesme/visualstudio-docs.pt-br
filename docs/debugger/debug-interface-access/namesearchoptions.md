---
title: NameSearchOptions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ceadd085a3099721e73e04dd09ea5a0b81ad1d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="namesearchoptions"></a>NameSearchOptions
Especifica as opções de pesquisa de símbolo e nomes de arquivos.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elementos  
 `nsNone`  
 Não há opções são especificadas.  
  
 `nsfCaseSensitive`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas.  
  
 `nsfCaseInsensitive`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas.  
  
 `nsfFNameExt`  
 Trata nomes como caminhos e aplica uma correspondência de nome de arquivo filename. ext.  
  
 `nsfRegularExpression`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas usando asteriscos (*) e pontos de interrogação (?) como caracteres curinga.  
  
 `nsfUndecoratedName`  
 Aplica-se somente a símbolos que têm não decorados e nomes decorados.  
  
## <a name="remarks"></a>Comentários  
 Os valores da enumeração são passados para os seguintes métodos:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)