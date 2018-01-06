---
title: "Hierarquia lexical de tipos de símbolos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6f9fe7b24a1e2bdd68d92f6dd22952df0d2a057
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hierarquia lexical de tipos de símbolos
A tabela a seguir mostra os tipos de símbolo na hierarquia lexical.  
  
## <a name="symbol-types"></a>Tipos de símbolo  
  
|Tipo de símbolo|Descrição|  
|-----------------|-----------------|  
|[Anotação](../../debugger/debug-interface-access/annotation.md)|Especifica um local anotado no código do programa.|  
|[Bloco](../../debugger/debug-interface-access/block.md)|Especifica os escopos aninhados em funções.|  
|`Compiland`|Especifica um `compiland` vinculado ao arquivo .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Especifica dados compiland que podem exigir carregar detalhes compiland adicionais e, portanto, incorrer em tempo de execução sobrecarga para recuperar.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Especifica as variáveis de ambiente adicionais significativas para a compilação do compiland.|  
|[Custom (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Especifica um símbolo definido pelo usuário.|  
|[Dados (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Especifica a essas variáveis como parâmetros, variáveis locais, variáveis globais e membros de classe.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Especifica o escopo global dos dados. corresponde a um arquivo inteiro .exe ou. dll.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Especifica uma função que tem um determinado ponto no qual a depuração é até o fim.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Especifica uma função que tem um determinado ponto no qual a depuração é começar.|  
|[Função (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Especifica uma função.|  
|[Rótulo (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Especifica um local no código do programa.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Especifica um símbolo externo que aparece ao criar o programa executável.|  
|[Conversão](../../debugger/debug-interface-access/thunk.md)|Especifica um `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Especifica um `namespace`identificador.|  
  
> [!NOTE]
>  Propriedades de símbolo adicionais podem estar disponíveis, dependendo do tipo de símbolo. Essas propriedades são listadas nos tópicos individuais de símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquia de classes de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Símbolos e marcações de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)