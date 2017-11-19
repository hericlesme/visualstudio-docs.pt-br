---
title: "Diretrizes do Visual Studio C++ Core verificador referência | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a129fcc5cfabb46dfa545d7f70e291b121ee5353
ms.sourcegitcommit: 24f81b8fb59722cf4a856005227f6a29bb2990cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="c-core-guidelines-checker-reference"></a>Referência de verificador de diretrizes do principal de C++
Esta seção lista os avisos do verificador de diretrizes de núcleos de C++. Para obter informações sobre análise de código, consulte [/Analyze (análise de código)](/cpp/build/reference/analyze-code-analysis) e [início rápido: análise de código para C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).  
  
**Observação**: alguns avisos pertencem a mais de um grupo, e não todos os avisos tem um tópico de referência.

## <a name="ownerpointer-group"></a>Grupo de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  Retorne um objeto no escopo, em vez de um alocados no heap se ele tem um construtor de movimento. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  Redefinir ou excluir explicitamente um proprietário\<T > ponteiro '% variável %'. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  Não exclua um proprietário\<T > que pode estar em estado inválido. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  Não atribua a um proprietário\<T > que pode estar em estado válido. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  Não atribua um ponteiro bruto para um proprietário\<T >. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  Preferir objetos de escopo, não heap-alocar desnecessariamente. Consulte [diretrizes de núcleos de C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  

[C26429 USE_NOTNULL](C26429.md)  
  O símbolo '% % de símbolo' nunca é testado para nullness, ele pode ser marcado como not_null. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  O símbolo '% % de símbolo' não é testado para nullness em todos os caminhos. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  O tipo da expressão '% % de expr' já está gsl::not_null. Não teste-o para nullness. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  

## <a name="rawpointer-group"></a>Grupo de RAW_POINTER
 
[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
Não atribua o resultado de uma alocação ou uma chamada de função com um proprietário\<T > valor de retorno para um ponteiro bruto, use proprietário<T> em vez disso. Consulte [diretrizes de núcleos de C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
Não exclua um ponteiro bruto não é um proprietário\<T >. Consulte [diretrizes de núcleos de C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw). 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   retornar um objeto no escopo, em vez de um alocados no heap se ele tem um construtor de movimento. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr). 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  Evite malloc e free(), preferir a versão nothrow do novo com delete. Consulte [diretrizes de núcleos de C++ R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  Evite chamar novas e excluir explicitamente, use std::make_unique\<T > em vez disso. Consulte [diretrizes de núcleos de C++ R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).  

[C26429 USE_NOTNULL](C26429.md)  
  O símbolo '% % de símbolo' nunca é testado para nullness, ele pode ser marcado como not_null. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  O símbolo '% % de símbolo' não é testado para nullness em todos os caminhos. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  O tipo da expressão '% % de expr' já está gsl::not_null. Não teste-o para nullness. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  Não use a aritmética de ponteiro. Use o alcance. Consulte [Bounds.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  A expressão 'expr % % %': Nenhuma matriz de decay do ponteiro. Consulte [Bounds.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

## <a name="uniquepointer-group"></a>Grupo de UNIQUE_POINTER
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  O parâmetro '% % do parâmetro' é uma referência ao `const` ponteiro exclusivo, use const T * ou const T & em vez disso. Consulte [diretrizes de núcleos de C++ R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  O parâmetro '% % do parâmetro' é uma referência ao ponteiro exclusivo e nunca é reatribuído ou redefinir, use * T ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Mover, copiar, reatribuir ou redefinir um ponteiro inteligente do local '% % de símbolo'. Consulte [diretrizes de núcleos de C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Ponteiro inteligente parâmetro '% Símbolo %' é usado somente para acesso contido ponteiro. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  

## <a name="sharedpointer-group"></a>Grupo de SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  Mover, copiar, reatribuir ou redefinir um ponteiro inteligente do local '% % de símbolo'. Consulte [diretrizes de núcleos de C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  Ponteiro inteligente parâmetro '% Símbolo %' é usado somente para acesso contido ponteiro. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  O parâmetro de ponteiro compartilhado '% % de símbolo' é passado por referência de rvalue. Passe por valor. Consulte [diretrizes de núcleos de C++ R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  Parâmetro de ponteiro compartilhado '% % de símbolo' é passado por referência e não redefinido ou reatribuído. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  O parâmetro de ponteiro compartilhado '% % de símbolo' não é copiado ou movido. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).  

## <a name="declaration-group"></a>DECLARAÇÃO de grupo
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  Inicializador global chama uma função constexpr não '% % de símbolo'. Consulte [diretrizes de núcleos de C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  Inicializador global acessa o objeto extern '% % de símbolo'. Consulte [diretrizes de núcleos de C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).  
  
## <a name="class-group"></a>CLASSE de grupo
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  Se você define ou excluir qualquer operação padrão no tipo '% % de símbolo', definir ou excluir todos eles. Consulte [diretrizes de núcleos de C++ c. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).  
  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  A função '% symbol_1% ' oculta uma função não virtual '% symbol_2% '. Consulte [diretrizes de núcleos de C++ C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).  
  
[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  O tipo '% % de símbolo' com uma função virtual precisa ou destruidor virtual ou protegido público. Consulte [diretrizes de núcleos de C++ C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).  

## <a name="type-group"></a>TIPO de grupo
    
[C26437 DONT_SLICE](C26437.md)  
  Não fatia. Consulte [diretrizes de núcleos de C++ ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).  

## <a name="style-group"></a>Grupo de estilo  
[C26438 NO_GOTO](C26438.md)  
  Evite `goto`. Consulte [diretrizes de núcleos de C++ ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).  
  
## <a name="function-group"></a>Grupo de funções
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  Esse tipo de função não pode gerar. Declare- `noexcept`. Consulte [diretrizes de núcleos de C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  A função '% % de símbolo' pode ser declarada `noexcept`. Consulte [diretrizes de núcleos de C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).  

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDADE
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 Objetos de proteção devem ser nomeados. Consulte [C++ principais diretrizes cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).  

## <a name="const-group"></a>Grupo CONST
    
C26460 USE_CONST_REFERENCE_ARGUMENTS:  
  O argumento de referência '% % de argumento' para a função '% % de função' pode ser marcado como `const`. Consulte [C++ principais diretrizes con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26461 USE_CONST_POINTER_ARGUMENTS: O argumento de ponteiro '% % de argumento' para a função '% % de função' pode ser marcado como um ponteiro para `const`. Consulte [C++ principais diretrizes con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE:  
  O valor apontado por '% variável %' é atribuído a apenas uma vez, marcá-la como um ponteiro para `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26463 USE_CONST_FOR_ELEMENTS:  
  Os elementos da matriz '% % de matriz' são atribuídos somente uma vez, os elementos de marca `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS:  
  Os valores apontados por elementos de matriz '% % de matriz' são atribuídos somente uma vez, os elementos de marca como ponteiro para `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  

C26496 USE_CONST_FOR_VARIABLE:  
  A variável '% variável %' é atribuída somente uma vez, marque-a como `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION:  
  Essa função de % de função pode ser marcada `constexpr` caso deseje a avaliação do tempo de compilação. Consulte [diretrizes de núcleos de C++ F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL:  
  Essa chamada de função % % de função pode usar `constexpr` caso deseje a avaliação do tempo de compilação. Consulte [C++ principais diretrizes con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).  

## <a name="type-group"></a>TIPO de grupo
C26465 NO_CONST_CAST_UNNECESSARY:  
  Não use `const_cast` para eliminar `const`. `const_cast`não é necessário; constness ou volatilidade não está sendo removida por essa conversão. Consulte [Type.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC:  
  Não use `static_cast` downcasts. Uma conversão de um tipo polimórfico deve usar dynamic_cast. Consulte [Type.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR:  
  Não use `reinterpret_cast`. Pode usar uma conversão de void * `static_cast`. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  Não use um `static_cast` para conversões aritméticas. Use a chave de inicialização, gsl::narrow_cast ou gsl::narow. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  Não fazer a conversão entre tipos de ponteiro em que o tipo de origem e o tipo de destino são os mesmos. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  Não fazer a conversão entre tipos de ponteiro quando a conversão pode ser implícita. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  Não use o estilo de função C conversões. Consulte [diretrizes de núcleos de C++ ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).  
     
C26490 NO_REINTERPRET_CAST:  
  Não use `reinterpret_cast`. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26491 NO_STATIC_DOWNCAST:  
  Não use `static_cast` downcasts. Consulte [Type.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26492 NO_CONST_CAST:  
  Não use `const_cast` para eliminar `const`. Consulte [Type.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
    
C26493 NO_CSTYLE_CAST:  
  Não use conversões do estilo C. Consulte [Type.4 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type). 
     
C26494 VAR_USE_BEFORE_INIT:  
  A variável '% variável %' não foi inicializado. Sempre inicialize um objeto. Consulte [Type.5 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
C26495 MEMBER_UNINIT:  
  A variável '% variável %' não foi inicializado. Sempre inicialize uma variável de membro. Consulte [Type.6 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).  
  
## <a name="bounds-group"></a>Grupo de limites

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  Não use a aritmética de ponteiro. Use o alcance. Consulte [Bounds.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING:  
  Apenas índice nas matrizes usando expressões de constante. Consulte [Bounds.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
C26483 STATIC_INDEX_OUT_OF_RANGE:  
  Valor % do valor está fora dos limites (0, associadas %) da variável '% variável %'. Apenas índice nas matrizes usando expressões de constante que estão dentro dos limites da matriz. Consulte [Bounds.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  A expressão 'expr % % %': Nenhuma matriz de decay do ponteiro. Consulte [Bounds.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).  
  
## <a name="see-also"></a>Consulte também  
[Usando os verificadores de diretrizes de núcleos de C++](using-the-cpp-core-guidelines-checkers.md)
