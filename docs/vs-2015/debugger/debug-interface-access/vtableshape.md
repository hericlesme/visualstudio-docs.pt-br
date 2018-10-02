---
title: VTableShape | Microsoft Docs
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
- VTableShape symbol
- SymTagVTableShape tag
ms.assetid: dd97f4c3-115d-46a9-b506-2531e30a0d8f
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2f40c276cbbac7815c3a21778e7980616c879cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462843"
---
# <a name="vtableshape"></a>VTableShape
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [VTableShape](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/vtableshape).  
  
O [VTable](../../debugger/debug-interface-access/vtable.md) símbolo tem um símbolo de filho de classe identificado pelo `SymTagVTableShape` marca.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir mostra as propriedades adicionais de válido para esse tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Se a classe de VTable é marcada como uma constante.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Número de entradas no VTable.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo compiland delimitador.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo léxico pai.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice de símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retorna `SymTagVTableShape` (um dos [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Se a classe de VTable é não alinhada.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Se a classe de VTable é marcada como volátil.|  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquia de classes de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTable](../../debugger/debug-interface-access/vtable.md)



