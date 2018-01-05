---
title: Operador de contexto do depurador (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cae22698a0200dc0971f45dbcfd7b28005f8f0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Operador de contexto no depurador do Visual Studio (C++)
Você pode usar o operador de contexto em C++ para qualificar um local de ponto de interrupção, o nome da variável ou expressão. O operador de contexto é útil para especificar um nome de um escopo externo que está oculto por um nome local.  
  
##  <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a>Sintaxe  
 Há duas maneiras de especificar o contexto:  
  
1.  {, [*módulo*]} *expressão*  
  
     As chaves devem conter duas vírgulas e o nome do módulo (executável ou DLL) ou o caminho completo.  
  
     Por exemplo, para definir um ponto de interrupção na função `SomeFunction` de EXAMPLE.dll:  
  
    ```C++  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2.  *módulo*! *expressão*  
  
    ```C++  
    EXAMPLE.dll!SomeFunction  
    ```  
  
-   *módulo* é o nome de um módulo. Você pode usar um caminho completo para resolver a ambiguidade entre módulos com o mesmo nome.  
  
     Se o *módulo* caminho inclui uma vírgula, um espaço inserido ou uma chave, você deve usar o caminho entre aspas para que o analisador de contexto possa reconhecer corretamente a cadeia de caracteres. As aspas simples são consideradas parte de um nome de arquivo do Windows, portanto, você deve usar aspas duplas. Por exemplo,  
  
    ```C++  
    {,,"a long, long, library name.dll"} g_Var  
    ```  
  
-   *expressão* é qualquer expressão válida de C++ que resolve para um destino válido, como um nome de função, o nome da variável ou o endereço de ponteiro em *módulo*.  
  
 Quando o avaliador de expressão localiza um símbolo em uma expressão, procura pelo símbolo na seguinte ordem:  
  
1.  Escopo léxico externo, começando com o bloco atual, série de instruções incluídas entre chaves e a continuação externa com o bloco delimitador. O bloco atual é o código que contém o local atual, endereço do ponteiro de instrução.  
  
2.  Escopo da função. A função atual.  
  
3.  Escopo da classe, se o local atual estiver dentro de uma função de membro C ++. O escopo da classe inclui todas as classes base. O avaliador de expressão usa regras de dominância normais.  
  
4.  Símbolos globais no módulo atual.  
  
5.  Símbolos públicos no programa atual.