---
title: NameSearchOptions | Microsoft Docs
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
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64f74880fe27cc71634508cbb6b272aea16517d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467562"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [NameSearchOptions](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/namesearchoptions).  
  
Especifica as opções de pesquisa para nomes de arquivo e símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 Nenhuma opção foi especificada.  
  
 `nsfCaseSensitive`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas.  
  
 `nsfCaseInsensitive`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas.  
  
 `nsfFNameExt`  
 Trata nomes como caminhos e aplica-se uma correspondência de nome de arquivo filename. ext.  
  
 `nsfRegularExpression`  
 Aplica-se uma correspondência de nome diferencia maiusculas de minúsculas usando asteriscos (*) e pontos de interrogação (?) como caracteres curinga.  
  
 `nsfUndecoratedName`  
 Aplica-se apenas aos símbolos que têm não decorados e nomes decorados.  
  
## <a name="remarks"></a>Comentários  
 Os valores dessa enumeração são passados para os seguintes métodos:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession:: FindFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



