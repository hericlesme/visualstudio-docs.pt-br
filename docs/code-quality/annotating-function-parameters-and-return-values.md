---
title: Anotando parâmetros de função e valores de retorno
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a06a987dc94ac4f3eb71d047ba33d410d7391a91
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="annotating-function-parameters-and-return-values"></a>Anotando parâmetros de função e valores de retorno
Este artigo descreve os usos comuns de anotações para parâmetros de função simples — escalares e ponteiros para estruturas e classes — e a maioria dos tipos de buffers.  Este artigo também mostra os padrões de uso comuns para anotações. Para anotações adicionais que estão relacionadas às funções, consulte [anotando o comportamento da função](../code-quality/annotating-function-behavior.md)

## <a name="pointer-parameters"></a>Parâmetros de ponteiro
 Para as anotações na tabela a seguir, quando um parâmetro de ponteiro está sendo anotado, o analisador informa um erro se o ponteiro for nulo.  Isso se aplica aos ponteiros e qualquer item de dados que aponte para.

 **As anotações e descrições**

-   `_In_`

     Anota parâmetros de entrada que são escalares, estruturas, ponteiros para estruturas e assim por diante.  Explicitamente, pode ser usado em escalares simples.  O parâmetro deve ser válido no estado de pré-lançamento e não será modificado.

-   `_Out_`

     Anota parâmetros de saída que são escalares, estruturas, ponteiros para estruturas e assim por diante.  Não use isso para um objeto que não é possível retornar um valor — por exemplo, um valor escalar que é transmitido por valor.  O parâmetro não precisa ser válido no estado anterior ao, mas deve ser válido no pós estado.

-   `_Inout_`

     Anota um parâmetro que será alterado pela função.  Ele deve ser válido no estado pré e pós-estado, mas tem valores diferentes antes e após a chamada. Aplique a um valor pode ser modificado.

-   `_In_z_`

     Um ponteiro para uma cadeia de caracteres terminada em nulo que é usado como entrada.  A cadeia de caracteres deve ser válida no estado de pré-lançamento.  Variantes de `PSTR`, que já tem as anotações corretas, são preferencial.

-   `_Inout_z_`

     Um ponteiro para uma matriz de caracteres terminada em nulo que será modificada.  Ele deve ser válido antes e após a chamada, mas o valor será considerado ter sido alterado.  O terminador nulo pode ser movido, mas apenas os elementos até o terminador nulo original podem ser acessados.

-   `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Um ponteiro para uma matriz, que é lido pela função.  A matriz é do tamanho `s` elementos, que deve ser válido.

     O `_bytes_` variante retorna o tamanho em bytes em vez de elementos. Use somente quando o tamanho não pode ser expressas como elementos.  Por exemplo, `char` cadeias de caracteres usaria o `_bytes_` variante somente se a função semelhantes que usa `wchar_t` seria.

-   `_In_reads_z_(s)`

     Um ponteiro para uma matriz que é terminada em nulo e tem um tamanho conhecido. Os elementos até o terminador nulo — ou `s` se houver um terminador nulo — deve ser válido no estado de pré-lançamento.  Se o tamanho é conhecido em bytes, o dimensionamento `s` pelo tamanho do elemento.

-   `_In_reads_or_z_(s)`

     Um ponteiro para uma matriz que é terminada em nulo ou tem um tamanho conhecido, ou ambos. Os elementos até o terminador nulo — ou `s` se houver um terminador nulo — deve ser válido no estado de pré-lançamento.  Se o tamanho é conhecido em bytes, o dimensionamento `s` pelo tamanho do elemento.  (Usado para o `strn` família.)

-   `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Um ponteiro para uma matriz de `s` elementos (bytes Resp.) que serão gravados pela função.  Os elementos da matriz não precisam ser válido em pré- estado e o número de elementos que são válidos no pós-estado não é especificado.  Se houver anotações no tipo de parâmetro, eles são aplicados em pós estado. Por exemplo, considere o código a seguir.

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     Neste exemplo, o chamador fornece um buffer de `size` elementos para `p1`.  `MyStringCopy` Alguns desses elementos torna válido. Além disso, o `_Null_terminated_` anotação em `PWSTR` significa que `p1` é terminada em nulo no pós estado.  Dessa forma, o número de elementos válidos é ainda bem definido, mas a contagem de um elemento específico não é necessária.

     O `_bytes_` variante retorna o tamanho em bytes em vez de elementos. Use somente quando o tamanho não pode ser expressas como elementos.  Por exemplo, `char` cadeias de caracteres usaria o `_bytes_` variante somente se a função semelhantes que usa `wchar_t` seria.

-   `_Out_writes_z_(s)`

     Um ponteiro para uma matriz de `s` elementos.  Os elementos não precisam ser válido em estado de pré-lançamento.  Pós-estado, os elementos de backup por meio de terminador nulo, que deve estar presente — deve ser válido.  Se o tamanho é conhecido em bytes, o dimensionamento `s` pelo tamanho do elemento.

-   `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Um ponteiro para uma matriz, que é lida e gravada para a função.  Ele é do tamanho `s` elementos e é válida no estado de pré e pós-estado.

     O `_bytes_` variante retorna o tamanho em bytes em vez de elementos. Use somente quando o tamanho não pode ser expressas como elementos.  Por exemplo, `char` cadeias de caracteres usaria o `_bytes_` variante somente se a função semelhantes que usa `wchar_t` seria.

-   `_Inout_updates_z_(s)`

     Um ponteiro para uma matriz que é terminada em nulo e tem um tamanho conhecido. Os elementos de backup por meio de terminador nulo, que deve estar presente — deve ser válido no estado pré e pós-estado.  O valor no pós-estado de deve ser diferente do valor no estado de pré-lançamento; Isso inclui o local do terminador nulo. Se o tamanho é conhecido em bytes, o dimensionamento `s` pelo tamanho do elemento.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Um ponteiro para uma matriz de `s` elementos.  Os elementos não precisam ser válido em estado de pré-lançamento.  Pós-estado, os elementos até o `c`elemento -ésimo deve ser válido.  Se o tamanho é conhecido em bytes, o dimensionamento `s` e `c` pelo tamanho do elemento ou use o `_bytes_` variante, que é definido como:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Em outras palavras, cada elemento que existe no buffer até `s` no estado de pré-lançamento é válida no pós estado de.  Por exemplo:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Um ponteiro para uma matriz, que é lida e gravada pela função.  Ele é do tamanho `s` elementos, que deve ser válido no estado de pré-lançamento, e `c` elementos devem ser válidos no pós estado.

     O `_bytes_` variante retorna o tamanho em bytes em vez de elementos. Use somente quando o tamanho não pode ser expressas como elementos.  Por exemplo, `char` cadeias de caracteres usaria o `_bytes_` variante somente se a função semelhantes que usa `wchar_t` seria.

-   `_Inout_updates_z_(s)`

     Um ponteiro para uma matriz que é terminada em nulo e tem um tamanho conhecido. Os elementos de backup por meio de terminador nulo, que deve estar presente — deve ser válido no estado pré e pós-estado.  O valor no pós-estado de deve ser diferente do valor no estado de pré-lançamento; Isso inclui o local do terminador nulo. Se o tamanho é conhecido em bytes, o dimensionamento `s` pelo tamanho do elemento.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Um ponteiro para uma matriz de `s` elementos.  Os elementos não precisam ser válido em estado de pré-lançamento.  Pós-estado, os elementos até o `c`elemento -ésimo deve ser válido.  Se o tamanho é conhecido em bytes, o dimensionamento `s` e `c` pelo tamanho do elemento ou use o `_bytes_` variante, que é definido como:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Em outras palavras, cada elemento que existe no buffer até `s` no estado de pré-lançamento é válida no pós estado de.  Por exemplo:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Um ponteiro para uma matriz, que é lida e gravada pela função.  Ele é do tamanho `s` elementos, que deve ser válido no estado de pré-lançamento, e `c` elementos devem ser válidos no pós estado.

     O `_bytes_` variante retorna o tamanho em bytes em vez de elementos. Use somente quando o tamanho não pode ser expressas como elementos.  Por exemplo, `char` cadeias de caracteres usaria o `_bytes_` variante somente se a função semelhantes que usa `wchar_t` seria.

-   `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Um ponteiro para uma matriz, que é lida e gravada pela função de tamanho `s` elementos. Definido como equivalente a:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Em outras palavras, cada elemento que existe no buffer até `s` no estado de pré-lançamento é válida no estado de pré e pós-estado.

     O `_bytes_` variante retorna o tamanho em bytes em vez de elementos. Use somente quando o tamanho não pode ser expressas como elementos.  Por exemplo, `char` cadeias de caracteres usaria o `_bytes_` variante somente se a função semelhantes que usa `wchar_t` seria.

-   `_In_reads_to_ptr_(p)`

     Um ponteiro para uma matriz para o qual a expressão `p`  -  `_Curr_` (ou seja, `p` menos `_Curr_`) é definido pelo idioma padrão apropriado.  Os elementos anteriores ao `p` deve ser válido no estado de pré-lançamento.

-   `_In_reads_to_ptr_z_(p)`

     Um ponteiro para uma matriz com terminação nula para o qual a expressão `p`  -  `_Curr_` (ou seja, `p` menos `_Curr_`) é definido pelo idioma padrão apropriado.  Os elementos anteriores ao `p` deve ser válido no estado de pré-lançamento.

-   `_Out_writes_to_ptr_(p)`

     Um ponteiro para uma matriz para o qual a expressão `p`  -  `_Curr_` (ou seja, `p` menos `_Curr_`) é definido pelo idioma padrão apropriado.  Os elementos anteriores ao `p` não precisa ser válido em estado de pré-lançamento e deve ser válido no pós estado.

-   `_Out_writes_to_ptr_z_(p)`

     Um ponteiro para uma matriz com terminação nula para o qual a expressão `p`  -  `_Curr_` (ou seja, `p` menos `_Curr_`) é definido pelo idioma padrão apropriado.  Os elementos anteriores ao `p` não precisa ser válido em estado de pré-lançamento e deve ser válido no pós estado.

## <a name="optional-pointer-parameters"></a>Parâmetros opcionais de ponteiro
 Quando uma anotação de parâmetro de ponteiro inclui `_opt_`, ele indica que o parâmetro pode ser nulo. Caso contrário, a anotação executa o mesmo que a versão que não inclua `_opt_`. Aqui está uma lista da `_opt_` variantes de anotações de parâmetro de ponteiro:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parâmetros de saída de ponteiro
 Parâmetros de saída de ponteiro exigem uma notação especial para desambiguar a nulidade no parâmetro e o local apontado para.

 **As anotações e descrições**

-   `_Outptr_`

     O parâmetro não pode ser nulo e no pós-estado de local apontado para não pode ser nulo e deve ser válido.

-   `_Outptr_opt_`

     O parâmetro pode ser nulo, mas no pós-estado de local apontado para não pode ser nulo e deve ser válido.

-   `_Outptr_result_maybenull_`

     O parâmetro não pode ser nulo e no pós-estado de local apontado para pode ser nulo.

-   `_Outptr_opt_result_maybenull_`

     O parâmetro pode ser nulo, e no pós-estado de local apontado para pode ser nulo.

 Na tabela a seguir, as subcadeias de caracteres adicionais são inseridas no nome da anotação para qualificar ainda mais o significado da anotação.  Diversas subcadeias de caracteres são `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, e `_to_`.

> [!IMPORTANT]
>  Se a interface que você estiver fazendo anotações for COM, use o formulário COM dessas anotações. Não use as anotações COM qualquer outra interface de tipo.

 **As anotações e descrições**

-   `_Outptr_result_z_`

     `_Outptr_opt_result_z_`

     `_Outptr_result_maybenull_z_`

     `_Ouptr_opt_result_maybenull_z_`

     O ponteiro retornado tem o `_Null_terminated_` anotação.

-   `_COM_Outptr_`

     `_COM_Outptr_opt_`

     `_COM_Outptr_result_maybenull_`

     `_COM_Outptr_opt_result_maybenull_`

     O ponteiro retornado tem semântica COM e, portanto, carrega um `_On_failure_` pós-condição em que o ponteiro retornado é nulo.

-   `_Outptr_result_buffer_(s)`

     `_Outptr_result_bytebuffer_(s)`

     `_Outptr_opt_result_buffer_(s)`

     `_Outptr_opt_result_bytebuffer_(s)`

     O ponteiro retornado aponta para um buffer válido de tamanho `s` elementos ou bytes.

-   `_Outptr_result_buffer_to_(s, c)`

     `_Outptr_result_bytebuffer_to_(s, c)`

     `_Outptr_opt_result_buffer_to_(s,c)`

     `_Outptr_opt_result_bytebuffer_to_(s,c)`

     O ponteiro retornado aponta para um buffer de tamanho `s` elementos ou bytes, dos quais a primeira `c` são válidos.

 Certas convenções de interface assumem que os parâmetros de saída são inúteis em caso de falha.  Exceto COM código explicitamente os formulários na tabela a seguir são preferenciais.  Para COM código, use as formas COM correspondentes são listadas na seção anterior.

 **As anotações e descrições**

-   `_Result_nullonfailure_`

     Modifica a outras anotações. O resultado é definido como nulo se a função falhar.

-   `_Result_zeroonfailure_`

     Modifica a outras anotações. O resultado é definido como zero se a função falhar.

-   `_Outptr_result_nullonfailure_`

     O ponteiro retornado aponta para um buffer válido se a função tiver êxito, ou nulo se a função falhar. Esta anotação é para um parâmetro não opcional.

-   `_Outptr_opt_result_nullonfailure_`

     O ponteiro retornado aponta para um buffer válido se a função tiver êxito, ou nulo se a função falhar. Esta anotação é para um parâmetro opcional.

-   `_Outref_result_nullonfailure_`

     O ponteiro retornado aponta para um buffer válido se a função tiver êxito, ou nulo se a função falhar. Esta anotação é para um parâmetro de referência.

## <a name="output-reference-parameters"></a>Parâmetros de referência de saída
 Um uso comum do parâmetro de referência é para parâmetros de saída.  Para parâmetros de referência de saída simples — por exemplo, `int&`—`_Out_` fornece a semântica correta.  No entanto, quando o valor de saída é um ponteiro — por exemplo `int *&`— como as anotações equivalentes ponteiro `_Outptr_ int **` não fornecer a semântica correta.  Para expressar maneira concisa a semântica de referência de parâmetros de saída para tipos de ponteiro, use essas anotações compostas:

 **As anotações e descrições**

-   `_Outref_`

     Resultado deve ser válido no pós- estado e não pode ser nulo.

-   `_Outref_result_maybenull_`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em pós estado.

-   `_Outref_result_buffer_(s)`

     Resultado deve ser válido no pós- estado e não pode ser nulo. Aponta para um buffer válido de tamanho `s` elementos.

-   `_Outref_result_bytebuffer_(s)`

     Resultado deve ser válido no pós- estado e não pode ser nulo. Aponta para um buffer válido de tamanho `s` bytes.

-   `_Outref_result_buffer_to_(s, c)`

     Resultado deve ser válido no pós- estado e não pode ser nulo. Aponta para o buffer de `s` elementos dos quais a primeira `c` são válidos.

-   `_Outref_result_bytebuffer_to_(s, c)`

     Resultado deve ser válido no pós- estado e não pode ser nulo. Aponta para o buffer de `s` bytes do que o primeiro `c` são válidos.

-   `_Outref_result_buffer_all_(s)`

     Resultado deve ser válido no pós- estado e não pode ser nulo. Aponta para um buffer válido de tamanho `s` elementos válidos.

-   `_Outref_result_bytebuffer_all_(s)`

     Resultado deve ser válido no pós- estado e não pode ser nulo. Aponta para um buffer válido de `s` bytes de elementos válidos.

-   `_Outref_result_buffer_maybenull_(s)`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em pós estado. Aponta para um buffer válido de tamanho `s` elementos.

-   `_Outref_result_bytebuffer_maybenull_(s)`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em pós estado. Aponta para um buffer válido de tamanho `s` bytes.

-   `_Outref_result_buffer_to_maybenull_(s, c)`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em pós estado. Aponta para o buffer de `s` elementos dos quais a primeira `c` são válidos.

-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em estado de post. Aponta para o buffer de `s` bytes do que o primeiro `c` são válidos.

-   `_Outref_result_buffer_all_maybenull_(s)`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em estado de post. Aponta para um buffer válido de tamanho `s` elementos válidos.

-   `_Outref_result_bytebuffer_all_maybenull_(s)`

     Resultado deve ser válido em pós-estado, mas pode ser nulo em estado de post. Aponta para um buffer válido de `s` bytes de elementos válidos.

## <a name="return-values"></a>Valores de Retorno
 O valor de retorno de uma função é semelhante a um `_Out_` parâmetro mas está em um nível diferente de de-reference, e você não deve considerar o conceito de ponteiro para o resultado.  Para as anotações a seguir, o valor de retorno é o objeto anotado — um escalar, um ponteiro para uma estrutura ou um ponteiro para um buffer. Essas anotações têm a mesma semântica correspondente `_Out_` anotação.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="other-common-annotations"></a>Outras anotações comuns
 **As anotações e descrições**

-   `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     O parâmetro, o campo ou o resultado está no intervalo (inclusivo) de `low` para `hi`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` que é aplicada ao objeto anotado junto com as condições de estado pré ou pós-estaduais apropriados.

    > [!IMPORTANT]
    >  Embora os nomes contêm "in" e "out", a semântica de `_In_` e `_Out_` fazer **não** se aplicam a essas anotações.

-   `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     O valor anotado é exatamente `expr`.  Equivalente a `_Satisfies_(_Curr_ == expr)` que é aplicada ao objeto anotado junto com as condições de estado pré ou pós-estaduais apropriados.

-   `_Struct_size_bytes_(size)`

     Aplica-se a uma declaração de classe ou estrutura.  Indica que um objeto válido desse tipo pode ser maior do que o tipo declarado, com o número de bytes que está sendo fornecido pelo `size`.  Por exemplo:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     O tamanho do buffer em bytes de um parâmetro `pM` do tipo `MyStruct *` , em seguida, é considerada como:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Recursos relacionados
 [Blog da equipe de análise de código](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Consulte também
 [Usando anotações de SAL para reduzir defeitos de código C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [Compreendendo SAL](../code-quality/understanding-sal.md) [anotando o comportamento da função](../code-quality/annotating-function-behavior.md) [anotando estruturas e Classes](../code-quality/annotating-structs-and-classes.md) [ Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md) [especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md) [funções intrínsecas](../code-quality/intrinsic-functions.md) [práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)