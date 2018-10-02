---
title: Hierarquia lexical de tipos de símbolo | Microsoft Docs
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
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d807841429a722f31f3aecdc08f1a0972b05378
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462859"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hierarquia lexical de tipos de símbolos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [hierarquia Lexical de tipos de símbolo](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/lexical-hierarchy-of-symbol-types).  
  
A tabela a seguir mostra os tipos de símbolo na hierarquia de léxico.  
  
## <a name="symbol-types"></a>Tipos de símbolo  
  
|Tipo de símbolo|Descrição|  
|-----------------|-----------------|  
|[Anotação](../../debugger/debug-interface-access/annotation.md)|Especifica um local anotado no código do programa.|  
|[Bloco](../../debugger/debug-interface-access/block.md)|Especifica os escopos aninhados em funções.|  
|`Compiland`|Especifica um `compiland` vinculado ao arquivo .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Especifica os dados de compiland que podem exigir Carregando detalhes compiland adicionais e, portanto, incorre em tempo de execução sobrecarga para recuperar.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Especifica as variáveis de ambiente adicionais significativas para a compilação de compiland.|  
|[Custom (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Especifica um símbolo definido pelo usuário.|  
|[Dados (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Especifica essas variáveis como parâmetros, variáveis locais, variáveis globais e membros de classe.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Especifica o escopo global dos dados. corresponde a um arquivo inteiro .exe ou. dll.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Especifica uma função que tem um ponto definido no qual a depuração é ao fim.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Especifica uma função que tem um ponto definido no qual a depuração deve iniciar.|  
|[Função (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Especifica uma função.|  
|[Rótulo (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Especifica um local no código do programa.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Especifica um símbolo externo que aparece ao compilar o programa executável.|  
|[Conversão](../../debugger/debug-interface-access/thunk.md)|Especifica um `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Especifica um `namespace`identificador.|  
  
> [!NOTE]
>  Propriedades de símbolo adicionais podem estar disponíveis, dependendo do tipo de símbolo. Essas propriedades são listadas nos tópicos individuais de símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquia de classes de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Símbolos e marcações de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



