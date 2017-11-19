---
title: "Noções básicas sobre SAL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1c6ac08b47bd5ad5e6dd84bbf78496c421a21a6
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="understanding-sal"></a>Noções básicas de SAL
A linguagem de anotação do código-fonte do Microsoft (SAL) fornece um conjunto de anotações que você pode usar para descrever como uma função usa as garantias de que ele faz quando ela estiver concluída, as suposições que faz sobre eles e seus parâmetros. As anotações são definidas no arquivo de cabeçalho `<sal.h>`. Análise de código do Visual Studio para C++ usa anotações de SAL para modificar a sua análise de funções. Para obter mais informações sobre SAL 2.0 para desenvolvimento de driver do Windows, consulte [SAL 2.0 anotações para Windows Drivers](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 Modo nativo, C e C++ fornecem apenas limitados aos desenvolvedores maneiras de expressar consistentemente intenção e invariance. Usando anotações de SAL, você pode descrever funções mais detalhadamente, para que os desenvolvedores que estão consumindo-los podem entender melhor como usá-los.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>O que é SAL e por que você deve usá-lo?  
 Simplificando, SAL é uma maneira de baixo custo para permitir que o compilador verifique seu código para você.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL torna código mais valiosos  
 SAL pode ajudar a fazer o seu design de código mais compreensível, para as pessoas e as ferramentas de análise de código. Considere este exemplo que mostra a função do tempo de execução C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Você pode dizer que essa função faz? Quando uma função é implementada ou a chamada, certas propriedades devem ser mantidas para garantir a exatidão do programa. Apenas olhando uma declaração, como mostrado no exemplo, você não sabe o que são. Sem anotações de SAL, você teria que dependem da documentação ou comentários de código. Aqui está a documentação do MSDN para `memcpy` diz:  
  
> "Cópias de contagem de bytes de origem para dest. Se a origem e destino se sobrepõem, o comportamento de memcpy é indefinido. Use memmove para lidar com regiões de sobreposição.   
> **Observação de segurança:** Certifique-se de que o buffer de destino é o mesmo tamanho ou maior que o buffer de origem. Para obter mais informações, consulte evitando saturações de Buffer".  
  
 A documentação contém algumas poucas informações que sugerem que seu código deve manter determinadas propriedades para garantir a exatidão do programa:  
  
-   `memcpy`Copia o `count` de bytes do buffer de origem para o buffer de destino.  
  
-   O buffer de destino deve ser pelo menos tão grande quanto o buffer de origem.  
  
 No entanto, o compilador não pode ler a documentação ou comentários informais. Ele não sabe que há uma relação entre dois buffers e `count`, e ele também não pode efetivamente adivinhar sobre uma relação. SAL pode fornecer mais clareza sobre as propriedades e a implementação da função, conforme mostrado aqui:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Observe que essas anotações se assemelha às informações na documentação do MSDN, mas eles são mais concisos e sigam um padrão de semântico. Ao ler esse código, você pode entender rapidamente as propriedades dessa função e como evitar problemas de segurança de saturação de buffer. Melhor ainda, os padrões de semânticos que fornece SAL podem melhorar a eficiência e a eficácia das ferramentas de análise de código automática na descoberta inicial de possíveis erros. Imagine que alguém grava essa implementação com bugs de `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Essa implementação contém um erro comum de desativar um. Felizmente, o autor de código incluído a anotação de tamanho do buffer SAL — uma ferramenta de análise de código pode capturar o bug analisando esta função apenas.  
  
### <a name="sal-basics"></a>Noções básicas SAL  
 SAL define quatro tipos básicos de parâmetros, que são categorizados por padrões de uso.  
  
|Categoria|Anotação do parâmetro|Descrição|  
|--------------|--------------------------|-----------------|  
|**A função de chamada de entrada**|`_In_`|Dados são passados para a função chamada e são tratados como somente leitura.|  
|**Entrada para chamada de função e de saída ao chamador**|`_Inout_`|Dados utilizáveis são passados para a função e potencialmente são modificados.|  
|**Saída ao chamador**|`_Out_`|O chamador só fornece espaço para a função de chamada gravar. A função chamada grava dados em que o espaço.|  
|**Saída de ponteiro para o chamador**|`_Outptr_`|Como **de saída ao chamador**. O valor retornado pela função chamada é um ponteiro.|  
  
 Essas anotações básico quatro podem ser feitas mais explícitas de várias maneiras. Por padrão, os parâmetros de ponteiro anotado deveriam para ser necessário, eles devem ser não nulos para a função tenha êxito. A variação mais usada de anotações básico indica que um parâmetro de ponteiro é opcional, se for NULL, a função ainda pode ter êxito ao fazer seu trabalho.  
  
 Esta tabela mostra como distinguir entre os parâmetros necessários e opcionais:  
  
||Parâmetros são necessários|Parâmetros são opcionais|  
|-|-----------------------------|-----------------------------|  
|**A função de chamada de entrada**|`_In_`|`_In_opt_`|  
|**Entrada para chamada de função e de saída ao chamador**|`_Inout_`|`_Inout_opt_`|  
|**Saída ao chamador**|`_Out_`|`_Out_opt_`|  
|**Saída de ponteiro para o chamador**|`_Outptr_`|`_Outptr_opt_`|  
  
 Essas anotações ajudam a identificar os valores possíveis não inicializados e usa de ponteiro nulo inválido de uma maneira formal e precisa. Passando NULL para um parâmetro necessário pode causar uma falha ou poderá causar um código de erro "Falha" a ser retornado. De qualquer forma, a função não pode ser bem-sucedida em fazer seu trabalho.  
  
## <a name="sal-examples"></a>Exemplos SAL  
 Esta seção mostra exemplos de código para as anotações de SAL básico.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Usando a ferramenta de análise de código do Visual Studio para localizar os defeitos  
 Nos exemplos, a ferramenta de análise de código do Visual Studio é usada junto com anotações de SAL para localizar os defeitos de código. Aqui está como fazer isso.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Para usar as ferramentas de análise de código do Visual Studio e SAL  
  
1.  No Visual Studio, abra um projeto de C++ que contém as anotações SAL.  
  
2.  Na barra de menus, escolha **criar**, **executar análise de código na solução**.  
  
     Considere o in\_ exemplo nesta seção. Se você executar a análise de código nele, esse aviso é exibido:  
  
    > **C6387 Valor de parâmetro inválido**   
    > 'aponte' pode ser '0': isso não adere à especificação para a função 'InCallee'.  
  
### <a name="example-the-in-annotation"></a>Exemplo: REC0 in\_ anotação  
 O `_In_` anotação indica que:  
  
-   O parâmetro deve ser válido e não será modificado.  
  
-   A função só será lido do buffer único elemento.  
  
-   O chamador deve fornecer o buffer e inicializá-lo.  
  
-   `_In_`Especifica "somente leitura". Um erro comum é aplicar `_In_` para um parâmetro que deve ter o `_Inout_` anotação em vez disso.  
  
-   `_In_`é permitido mas ignorado pelo analisador em não ponteiro escalares.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Se você usar a análise de código do Visual Studio neste exemplo, ele valida que os chamadores transmitir um ponteiro de não-nulo para um buffer inicializado para `pInt`. Nesse caso, `pInt` ponteiro não pode ser NULL.  
  
### <a name="example-the-inopt-annotation"></a>Exemplo: O _In_opt\_ anotação  
 `_In_opt_`é o mesmo que `_In_`, exceto que o parâmetro de entrada tem permissão para ser NULL e, portanto, a função deve verificar isso.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Análise de código do Visual Studio valida que a função verifica NULL antes que ele acesse o buffer.  
  
### <a name="example-the-out-annotation"></a>Exemplo: O out\_ anotação  
 `_Out_`oferece suporte a um cenário comum em que um ponteiro não nulo que aponta para um buffer de elemento é transmitido e a função inicializa o elemento. O chamador não precisa inicializar o buffer antes da chamada; a função chamada promete inicializá-lo antes de retornar.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Ferramenta de análise de código do Visual Studio valida que o chamador passa um ponteiro não nulo para um buffer para `pInt` e que o buffer é inicializado pela função antes de retornar.  
  
### <a name="example-the-outopt-annotation"></a>Exemplo: O _Out_opt\_ anotação  
 `_Out_opt_`é o mesmo que `_Out_`, exceto que o parâmetro pode ser NULL e, portanto, a função deve verificar isso.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Análise de código do Visual Studio valida que essa função verifica nulo antes de `pInt` está referenciado e se `pInt` não for NULL, que o buffer é inicializado pela função antes de retornar.  
  
### <a name="example-the-inout-annotation"></a>Exemplo: REC0 inout\_ anotação  
 `_Inout_`é usado para anotar um parâmetro de ponteiro que pode ser alterado pela função. O ponteiro deve apontar para dados inicializados válidos antes da chamada e, mesmo se ele for alterado, ele ainda deve ter um valor válido no retorno. A anotação Especifica que a função pode ler e gravar no buffer de um elemento livremente. O chamador deve fornecer o buffer e inicializá-lo.  
  
> [!NOTE]
>  Como `_Out_`, `_Inout_` devem se aplicar a um valor pode ser modificado.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Análise de código do Visual Studio valida que os chamadores transmitir um ponteiro de não-nulo para um buffer inicializado para `pInt`e que, antes de retorno, `pInt` ainda não for nulo e o buffer é inicializado.  
  
### <a name="example-the-inoutopt-annotation"></a>Exemplo: O _Inout_opt\_ anotação  
 `_Inout_opt_`é o mesmo que `_Inout_`, exceto que o parâmetro de entrada tem permissão para ser NULL e, portanto, a função deve verificar isso.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Análise de código do Visual Studio valida que essa função verifica NULL antes que ele acesse o buffer e se `pInt` não for NULL, que o buffer é inicializado pela função antes de retornar.  
  
### <a name="example-the-outptr-annotation"></a>Exemplo: O _Outptr\_ anotação  
 `_Outptr_`é usado para anotar um parâmetro que tem como objetivo retornar um ponteiro.  O próprio parâmetro não deve ser NULL e a função chamada retorna um ponteiro NULL não nele e esse ponteiro aponta para dados inicializados.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Análise de código do Visual Studio valida que o chamador passa um ponteiro não nula `*pInt`, e que o buffer é inicializado pela função antes de retornar.  
  
### <a name="example-the-outptropt-annotation"></a>Exemplo: O _Outptr_opt\_ anotação  
 `_Outptr_opt_`é o mesmo que `_Outptr_`, exceto que o parâmetro é opcional, o chamador pode passar um ponteiro nulo para o parâmetro.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Análise de código do Visual Studio valida que essa função verifica NULL antes `*pInt` está referenciado, e que o buffer é inicializado pela função antes de retornar.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Exemplo: O _Success\_ anotação em combinação com out\_  
 As anotações podem ser aplicadas à maioria dos objetos.  Em particular, você pode anotar uma função inteira.  Uma das características de uma função mais óbvias é que ele pode ter êxito ou falhar. Mas, como a associação entre um buffer e seu tamanho, C/C++ não pode expressar função êxito ou falha. Usando o `_Success_` anotação, você pode dizer o sucesso de uma função.  O parâmetro para o `_Success_` anotação é apenas uma expressão que quando for verdadeiro indica que a função foi bem-sucedida. A expressão pode ser qualquer coisa que o analisador de anotação pode manipular. Os efeitos das anotações depois que a função retorna só são aplicáveis quando a função tiver êxito. Este exemplo mostra como `_Success_` interage com `_Out_` para fazer a coisa certa. Você pode usar a palavra-chave `return` representar o valor de retorno.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 O `_Out_` anotação faz a análise de código do Visual Studio para validar que o chamador passa um ponteiro não nulo para um buffer para `pInt`, e que o buffer é inicializado pela função antes de retornar.  
  
## <a name="sal-best-practice"></a>Prática recomendada de SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Adicionando anotações para o código existente  
 SAL é uma tecnologia avançada que pode ajudar a melhorar a segurança e a confiabilidade do seu código. Depois que você saiba SAL, você pode aplicar a nova habilidade para seu trabalho diário. No novo código, você pode usar as especificações de SAL por design em todo; no código anterior, você pode adicionar anotações de forma incremental e, portanto, aumentar as vantagens toda vez que você atualizar.  
  
 Cabeçalhos públicos da Microsoft já são anotados. Portanto, sugerimos que em seus projetos você primeiro anotar funções do nó de folha e funções que chamam as APIs do Win32 para aproveitar ao máximo.  
  
### <a name="when-do-i-annotate"></a>Quando anotar?  
 Aqui estão algumas diretrizes:  
  
-   Anote todos os parâmetros de ponteiro.  
  
-   Anote anotações de intervalo de valores para que a análise de código pode garantir a segurança do buffer e ponteiro.  
  
-   Anotação de regras de bloqueio e bloqueio efeito colateral. Para obter mais informações, consulte [anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md).  
  
-   Anotação de propriedades do driver e outras propriedades específicas do domínio.  
  
 Ou você pode anotar todos os parâmetros para tornar sua intenção clear em todo e para tornar mais fácil verificar que tem sido feitas anotações.  
  
## <a name="related-resources"></a>Recursos relacionados  
 [Blog da equipe de análise de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando estruturas e Classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)