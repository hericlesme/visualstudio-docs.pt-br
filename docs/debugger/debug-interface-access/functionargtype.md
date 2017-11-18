---
title: FunctionArgType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: FunctionArgType symbol
ms.assetid: 9f072fd3-0b99-405c-af99-fd44cd56fd73
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9421481a90ad45e6ddca0623483e681d0c90422
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="functionargtype"></a>FunctionArgType
Cada parâmetro de uma função é identificado por um `SymTagFunctionArgType` símbolo.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir mostra as propriedades adicionais de válido para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Símbolo FunctionType pai.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID do símbolo classe pai.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de circunscrição [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo lexical pai.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice de símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retorna `SymTagFunctionArgType` (um do [SymTagEnum enumeração](../../debugger/debug-interface-access/symtagenum.md) valores).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Tipo do parâmetro.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID do símbolo de tipo.|  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquia de classes de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [FunctionType](../../debugger/debug-interface-access/functiontype.md)