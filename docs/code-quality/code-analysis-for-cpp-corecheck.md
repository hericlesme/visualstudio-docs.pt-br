---
title: Referência do Visual Studio C++ Core diretrizes verificador
ms.date: 03/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 09abcf8b1ece1360056a479df568db3a4e569ff1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917011"
---
# <a name="c-core-guidelines-checker-reference"></a>Referência de verificador de diretrizes do principal de C++

Esta seção lista os avisos do verificador de diretrizes de núcleos de C++. Para obter informações sobre análise de código, consulte [/Analyze (análise de código)](/cpp/build/reference/analyze-code-analysis) e [início rápido: análise de código para C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Alguns avisos pertencem a mais de um grupo, e não todos os avisos tem um tópico de referência completa.

## <a name="ownerpointer-group"></a>Grupo de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) retornar um objeto no escopo, em vez de um alocados no heap se ele tem um construtor de movimento. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) redefinir ou excluir explicitamente um proprietário\<T > ponteiro '% variável %'. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) não exclua um proprietário\<T > que pode estar em estado inválido. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) não atribuir um proprietário\<T > que pode estar em estado válido. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) não atribuir um ponteiro bruto para um proprietário\<T >. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) preferem objetos de escopo, não heap-alocar desnecessariamente. Consulte [diretrizes de núcleos de C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) símbolo '% % de símbolo' nunca é testado para nullness, ele pode ser marcado como not_null. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) símbolo '% % de símbolo' não foi testado para nullness em todos os caminhos. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) o tipo da expressão '% % de expr' já está gsl::not_null. Não teste-o para nullness. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>RAW_POINTER Group

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) não atribua o resultado de uma alocação ou uma chamada de função com um proprietário\<T > valor de retorno para um ponteiro bruto; use proprietário\<T > em vez disso. Consulte [diretrizes de núcleos de C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) não exclua um ponteiro bruto não é um proprietário\<T >. Consulte [diretrizes de núcleos de C++ I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   retornar um objeto no escopo, em vez de um alocados no heap se ele tem um construtor de movimento. Consulte [diretrizes de núcleos de C++ R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) evitar malloc e free(), preferir a versão nothrow do novo com delete. Consulte [diretrizes de núcleos de C++ R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Evite chamar novas e excluir explicitamente, use std::make_unique\<T > em vez disso. Consulte [diretrizes de núcleos de C++ R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) símbolo '% % de símbolo' nunca é testado para nullness, ele pode ser marcado como not_null. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) símbolo '% % de símbolo' não foi testado para nullness em todos os caminhos. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) o tipo da expressão '% % de expr' já está gsl::not_null. Não teste-o para nullness. Consulte [diretrizes de núcleos de C++ F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) não usar aritmética de ponteiro. Use o alcance. Consulte [Bounds.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
A expressão 'expr % % %': Nenhuma matriz de decay do ponteiro. Consulte [Bounds.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>UNIQUE_POINTER Group

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) o parâmetro '% % do parâmetro' é uma referência ao `const` ponteiro exclusivo, use const T * ou const T & em vez disso. Consulte [diretrizes de núcleos de C++ R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) o parâmetro '% % do parâmetro' é uma referência ao ponteiro exclusivo e nunca é reatribuído ou redefinir, use * T ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) mover, copiar, reatribuir ou redefinir um ponteiro inteligente do local '% % de símbolo'. Consulte [diretrizes de núcleos de C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parâmetro de ponteiro inteligente '% % de símbolo' é usado somente para acessar o ponteiro independente. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>SHARED_POINTER Group

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) mover, copiar, reatribuir ou redefinir um ponteiro inteligente do local '% % de símbolo'. Consulte [diretrizes de núcleos de C++ R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) parâmetro de ponteiro inteligente '% % de símbolo' é usado somente para acessar o ponteiro independente. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parâmetro de ponteiro compartilhado '% % de símbolo' é passado por referência de rvalue. Passe por valor. Consulte [diretrizes de núcleos de C++ R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parâmetro de ponteiro compartilhado '% % de símbolo' é passado por referência e não redefinido ou reatribuído. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parâmetro de ponteiro compartilhado '% % de símbolo' não é copiado ou movido. Use T * ou T & em vez disso. Consulte [diretrizes de núcleos de C++ R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DECLARAÇÃO de grupo

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) inicializador Global chama uma função constexpr não '% % de símbolo'. Consulte [diretrizes de núcleos de C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inicializador Global acessa o objeto extern '% % de símbolo'. Consulte [diretrizes de núcleos de C++ I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Evite sem nome objetos com construção personalizada e destruição. Consulte [ES.84: não (tente) declarar uma variável local sem nome](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>CLASSE de grupo

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) se você define ou excluir qualquer operação padrão no tipo '% % de símbolo', definir ou excluir todos eles. Consulte [diretrizes de núcleos de C++ c. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) função '% % de símbolo' deve ser marcada com 'override'. Consulte [C.128: funções virtuais devem especificar exatamente um dos virtual, substituição, ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) função '% symbol_1% ' oculta uma função não virtual '% symbol_2% '. Consulte [diretrizes de núcleos de C++ C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) função '% % de símbolo' deve especificar exatamente um 'virtual', 'override' ou 'final'. Consulte [C.128: funções virtuais devem especificar exatamente um dos virtual, substituição, ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) o tipo '% % de símbolo' com uma função virtual precisa ou destruidor virtual ou protegido público. Consulte [diretrizes de núcleos de C++ C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) substituindo destruidor não deve usar explícita 'override' ou 'virtuais' especificadores. Consulte [C.128: funções virtuais devem especificar exatamente um dos virtual, substituição, ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>TIPO de grupo

[C26437 DONT_SLICE](C26437.md) não fatiar. Consulte [diretrizes de núcleos de C++ ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Grupo de estilo

[C26438 NO_GOTO](C26438.md) evitar `goto`. Consulte [diretrizes de núcleos de C++ ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupo de funções

[C26439 SPECIAL_NOEXCEPT](C26439.md) esse tipo de função não pode gerar. Declare- `noexcept`. Consulte [diretrizes de núcleos de C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) função '% % de símbolo' pode ser declarada `noexcept`. Consulte [diretrizes de núcleos de C++ f. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) a função é declarada **noexcept** mas chama uma função que pode gerar exceções.
Consulte [diretrizes de núcleos de C++: f. 6: se sua função pode não lançar, declare noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDADE

[C26441 NO_UNNAMED_GUARDS](C26441.md) objetos de proteção devem ser nomeados. Consulte [C++ principais diretrizes cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Grupo CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) o argumento de referência '% % de argumento' para a função '% % de função' pode ser marcado como `const`. Consulte [C++ principais diretrizes con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): O argumento de ponteiro '% % de argumento' para a função '% % de função' pode ser marcado como um ponteiro para `const`. Consulte [C++ principais diretrizes con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) o valor apontado por '% variável %' é atribuído a apenas uma vez, marcá-la como um ponteiro para `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) os elementos da matriz '% % de matriz' são atribuídos somente uma vez, os elementos de marca `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) os valores apontados por elementos de matriz '% % de matriz' são atribuídos somente uma vez, os elementos de marca como ponteiro para `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) a variável '% variável %' é atribuída somente uma vez, marque-a como `const`. Consulte [C++ principais diretrizes con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) essa função de % de função pode ser marcada `constexpr` caso deseje a avaliação do tempo de compilação. Consulte [diretrizes de núcleos de C++ F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) pode usar essa função chamada % função `constexpr` caso deseje a avaliação do tempo de compilação. Consulte [C++ principais diretrizes con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO de grupo

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) não use `const_cast` para eliminar `const`. `const_cast` não é necessário; constness ou volatilidade não está sendo removida por essa conversão. Consulte [Type.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) não use `static_cast` downcasts. Uma conversão de um tipo polimórfico deve usar dynamic_cast. Consulte [Type.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) Don't use `reinterpret_cast`. Pode usar uma conversão de void * `static_cast`. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) não use um `static_cast` para conversões aritméticas. Use a chave de inicialização, gsl::narrow_cast ou gsl::narow. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) não conversão entre tipos de ponteiro em que o tipo de origem e o tipo de destino são os mesmos. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) não conversão entre tipos de ponteiro quando a conversão pode ser implícita. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) não usar C conversões de estilo de função. Consulte [diretrizes de núcleos de C++ ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) não use `reinterpret_cast`. Consulte [Type.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) não use `static_cast` downcasts. Consulte [Type.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) não use `const_cast` para eliminar `const`. Consulte [Type.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) não usar conversões do estilo C. Consulte [Type.4 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) variável '% variável %' não foi inicializado. Sempre inicialize um objeto. Consulte [Type.5 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) variável '% variável %' não foi inicializado. Sempre inicialize uma variável de membro. Consulte [Type.6 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupo de limites

[C26446 USE_GSL_AT](c26446.md) preferir usar `gsl::at()` em vez do operador subscrito desmarcada. Consulte [diretrizes de núcleos de C++: Bounds.4: não use funções de biblioteca padrão e tipos que não são verificadas limites](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Não use a aritmética de ponteiro. Use o alcance. Consulte [Bounds.1 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) índice somente em matrizes usando expressões de constante. Consulte [Bounds.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) valor % do valor está fora dos limites (0, associadas %) da variável '% variável %'. Apenas índice nas matrizes usando expressões de constante que estão dentro dos limites da matriz. Consulte [Bounds.2 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) expressão 'expr % % %': Nenhuma matriz de decay do ponteiro. Consulte [Bounds.3 de diretrizes de núcleos de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupo de GSL

[C26445 NO_SPAN_REF](c26445.md) uma referência a `gsl::span` ou `std::string_view` pode ser uma indicação de um problema de tempo de vida.
Consulte [C++ Core diretrizes GSL.view: modos de exibição](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) preferir usar `gsl::at()` em vez do operador subscrito desmarcada. Consulte [diretrizes de núcleos de C++: Bounds.4: não use funções de biblioteca padrão e tipos que não são verificadas limites](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) considere usar `gsl::finally` se destina-se a ação final. Consulte [diretrizes de núcleos de C++: GSL.util: utilitários](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` ou `std::string_view` criado a partir de um temporário será inválido quando temporárias são invalidadas. Consulte [diretrizes de núcleos de C++: GSL.view: exibições](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Avisos preteridos

Os seguintes avisos estão presentes em um conjunto de regra experimental antecipada do verificador de diretrizes de núcleos, mas agora são preteridos e podem ser ignorados. Os avisos são substituídos pelos avisos da lista acima.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Consulte também
[Usando os verificadores de diretrizes de núcleos de C++](using-the-cpp-core-guidelines-checkers.md)
