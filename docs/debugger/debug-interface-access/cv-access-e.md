---
title: CV_access_e | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6112c72836c718dbd97ddfb62504186fdcf6ca33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="cvaccesse"></a>CV_access_e
Especifica o escopo de visibilidade (nível de acesso) de funções de membro e variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_private  
 Membro possui acesso privado.  
  
 CV_protected  
 Membro tenha acesso protegido.  
  
 CV_public  
 Membro tem acesso público.  
  
## <a name="remarks"></a>Comentários  
 O `friend` especificador de acesso não é incluído aqui porque ele é normalmente usado por funções não membro que têm acesso aos elementos protegidos e privados da classe. Use o [: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método para localizar símbolos com `SymTagFriend` acesso.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [: Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)