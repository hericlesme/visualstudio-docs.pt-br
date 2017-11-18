---
title: Exe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab02eacffe01c267a2f3d4ff463b729591bb8b19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="exe"></a>Exe
Exe é símbolos sem qualquer um de um léxico ou classe pai, o único que representa o escopo global do arquivo .exe ou. dll. Há apenas um símbolo com o `SymTagExe` marca por arquivo. O [: Get_globalscope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) método retorna o símbolo.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Idade desse executável.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID`desse executável.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE`Se o arquivo de símbolo associado com este executável contém tipos C (apenas no v DIA SDK 8.0 ou posterior).|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE`Se os símbolos privados tem sido removidos o arquivo de símbolo associado a este executável (somente no v DIA SDK 8.0 ou posterior).|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Valor que indica a CPU de destino (um do [enumeração CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) valores).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome do arquivo .exe.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Assinatura do executável.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Caminho completo para o arquivo. PDB ou. dbg de .exe do arquivo.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice de símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retorna `SymTagExe` (um do [SymTagEnum enumeração](../../debugger/debug-interface-access/symtagenum.md) valores).|  
  
## <a name="see-also"></a>Consulte também  
 [: Get_globalscope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Hierarquia lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)