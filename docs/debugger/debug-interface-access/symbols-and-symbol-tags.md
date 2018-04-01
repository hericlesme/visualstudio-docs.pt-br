---
title: Símbolos e marcações de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c3e51d02171455cd5b0b6051ed3b05c6d95278ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="symbols-and-symbol-tags"></a>Símbolos e marcações de símbolos
Informações de depuração sobre um programa compilado são armazenadas no arquivo de banco de dados (. PDB) programa como símbolos que podem ser acessados usando as APIs do SDK de acesso de Interface de depuração (DIA). Todos os símbolos têm um [: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e um [: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) propriedade. O `symTag` propriedade indica o tipo de símbolo conforme definido pelo [SymTagEnum enumeração](../../debugger/debug-interface-access/symtagenum.md) enumeração. O `symIndexId` propriedade é um `DWORD` valor que contém o identificador exclusivo para cada instância de um símbolo.  
  
 Símbolos também têm propriedades que podem especificar informações adicionais sobre o símbolo, bem como as referências a outros símbolos, geralmente um [: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ou [: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando você consulta uma propriedade que contém uma referência, a referência é retornada como um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto. Essas propriedades são sempre combinadas com outra propriedade com o mesmo nome mas suffixed com "Id", por exemplo, [: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). As tabelas no [locais de símbolo](../../debugger/debug-interface-access/symbol-locations.md), [hierarquia Lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), e [classe hierarquia de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) descrever as propriedades para cada um dos diferentes tipos de símbolos. Essas propriedades podem ter informações relevantes sobre ou referências a outros símbolos. Porque o `*Id` propriedades são identificadores ordinal simplesmente numéricos de suas propriedades relacionadas, eles são omitidos de discussões ainda mais. Eles são chamados somente quando necessário para fins de esclarecimento de parâmetro.  
  
 Ao tentar acessar a propriedade, se nenhum erro ocorre e a propriedade de símbolo foi atribuída um valor, a propriedade "get" método retornará `S_OK`. Um valor de retorno `S_FALSE` indica que a propriedade não é válida para o símbolo atual.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)  
 Descreve os diferentes tipos de locais que pode ter um símbolo.  
  
 [Hierarquia lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Descreve os tipos de símbolo que formam hierarquias lexicais como arquivos, módulos e funções.  
  
 [Hierarquia de classes de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Descreve os tipos de símbolo que correspondem aos elementos de linguagem diferentes, como tipos de retorno de classes, matrizes e função.  
  
## <a name="see-also"></a>Consulte também  
 [SDK de Acesso à Interface de Depuração](../../debugger/debug-interface-access/debug-interface-access-sdk.md)