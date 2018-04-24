---
title: Expressões no depurador | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dccd4af0c14787ef34c1c558f83ecb2d6f0c1cea
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Expressões no depurador do Visual Studio
O depurador do Visual Studio inclui avaliadores de expressão que funcionam quando você insere uma expressão no **QuickWatch** caixa de diálogo, **inspecionar** janela, ou **imediato** janela. Os avaliadores de expressão também estão em funcionamento no **pontos de interrupção** janela e muitos outros locais no depurador.
  
 As seções a seguir fornecem detalhes sobre expressões em idiomas diferentes.  
  
## <a name="f-expressions-are-not-supported"></a>Não há suporte para expressões F #  
 Expressões de F # não são reconhecidas. Se você estiver depurando código F #, você precisa converter as expressões em c# sintaxe antes de inserir expressões em uma caixa de diálogo ou janela de depurador. Quando você converte expressões do F # para c#, certifique-se de lembrar que c# usa o `==` operador para testar a igualdade, enquanto o F # usa o único `=`.  
  
## <a name="c-expressions"></a>Expressões de C++  
 Para obter informações sobre como usar operadores de contexto com expressões em C++, consulte [o operador de contexto (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Não há suporte para expressões em C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Construtores, destruidores e conversões  
 Você não pode chamar um construtor ou destrutor de um objeto, explicitamente ou implicitamente. Por exemplo, a expressão a seguir chama explicitamente um construtor e resulta em uma mensagem de erro:  
  
```C++  
my_date( 2, 3, 1985 )  
```  
  
 Você não pode chamar uma função de conversão se o destino da conversão for uma classe. Essa conversão envolve a construção de um objeto. Por exemplo, se `myFraction` for uma instância de `CFraction`, que define o operador da função de conversão `FixedPoint`, a expressão a seguir resultará em erro:  
  
```C++  
(FixedPoint)myFraction  
```  
  
 Você não pode chamar o novo ou excluir operadores. Por exemplo, não há suporte para a expressão a seguir:  
  
```C++  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Macros de pré-processador  
 Não há suporte para macros de pré-processador no depurador. Por exemplo, se uma constante `VALUE` é declarado como: `#define VALUE 3`, você não pode usar `VALUE` no **inspecionar** janela. Para evitar essa limitação, você deve substituir `#define`com enums e funções sempre que possível.  
  
### <a name="using-namespace-declarations"></a>usando declarações de namespace  
 Não é possível usar `using namespace` declarações.  Para acessar um nome de tipo ou a variável fora do espaço no momento, você deve usar o nome totalmente qualificado.  
  
### <a name="anonymous-namespaces"></a>Namespaces anônimos  
 Não há suporte para namespaces anônimos. Se você tiver o código a seguir, você não pode adicionar `test` à janela de inspeção:  
  
```C++  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
###  <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Usando funções intrínsecas do depurador para manter o estado  
 As funções intrínsecas do depurador oferecem uma maneira de chamar determinadas funções C/C++ em expressões sem alterar o estado do aplicativo.  
  
 Funções intrínsecas do depurador:  
  
-   São certamente seguras: executar uma função intrínseca do depurador não corromperá o processo que está sendo depurado.  
  
-   São permitidas em todas as expressões, mesmo em cenários onde os efeitos colaterais e a avaliação de função não são permitidos.  
  
-   Trabalham em cenários onde as chamadas de funções normais não são possíveis, por exemplo, depurar um minidespejo.  
  
 As funções intrínsecas do depurador também podem tornar mais convenientes as expressões de avaliação. Por exemplo, `strncmp(str, "asd")` é muito mais fácil escrever em uma condição de ponto de interrupção de `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )  
  
|Área|Funções intrínsecas|  
|----------|-------------------------|  
|**Comprimento de cadeia de caracteres**|strlen, wcslen, strnlen, wcsnlen|  
|**Comparação de cadeia de caracteres**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Pesquisa de cadeia de caracteres**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Essas funções exigem que o processo que está sendo depurado seja executado no Windows 8. Depurar os arquivos de despejo gerados a partir de um dispositivo do Windows 8 também exige que o computador do Visual Studio esteja executando o Windows 8. No entanto, se você estiver depurando um dispositivo do Windows 8 remotamente, o computador do Visual Studio poderá executar o Windows 7.|  
|**Diversos**|__log2<br /><br /> Retorna a base 2 de log de um inteiro especificado, arredondada para o menor inteiro próximo.|  
  
## <a name="ccli---unsupported-expressions"></a>C + + CLI - não há suporte para expressões  
  
-   Não há suporte para conversões que envolvem ponteiros ou conversões definidas pelo usuário.  
  
-   Não há suporte para a atribuição e comparação de objeto.  
  
-   Não há suporte para funções sobrecarregadas e operadores sobrecarregados.  
  
-   Não há suporte para conversões boxing e unboxing.  
  
-   `Sizeof` Não há suporte para o operador.  
  
## <a name="c---unsupported-expressions"></a>C# - não há suporte para expressões  
  
### <a name="dynamic-objects"></a>Objetos dinâmicos  
 Você pode usar variáveis em expressões de depurador estaticamente são digitadas como dinâmica. Quando os objetos que implementam o [IDynamicMetaObjectProvider Interface](http://msdn.microsoft.com/Library/e887a72d-ebe2-4253-a7e8-3d8d05154647) são avaliadas na janela Inspeção, uma exibição dinâmica nó seja adicionado. O nó do Modo de Exibição Dinâmico exibe membros do objeto, mas não permite editar os valores dos membros.  
  
 Os seguintes recursos de objetos dinâmicos não têm suporte:  
  
-   Os operadores compostos `+=`, `-=`, `%=`, `/=`, e `*=`  
  
-   Várias conversões, inclusive conversões numéricas e conversões de tipo de argumento  
  
-   Chamadas de método com mais de dois argumentos  
  
-   Getters da propriedade com mais de dois argumentos  
  
-   Setters de propriedade com argumentos  
  
-   Atribuição a um indexador  
  
-   Operadores boolianos `&&` e `||`  
  
### <a name="anonymous-methods"></a>Métodos anônimos  
 Não há suporte para a criação de novos métodos anônimos.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - não há suporte para expressões  
  
### <a name="dynamic-objects"></a>Objetos dinâmicos  
 Você pode usar variáveis em expressões de depurador estaticamente são digitadas como dinâmica. Quando os objetos que implementam o [IDynamicMetaObjectProvider Interface](http://msdn.microsoft.com/Library/e887a72d-ebe2-4253-a7e8-3d8d05154647) são avaliadas na janela Inspeção, uma exibição dinâmica nó seja adicionado. O nó do Modo de Exibição Dinâmico exibe membros do objeto, mas não permite editar os valores dos membros.  
  
 Os seguintes recursos de objetos dinâmicos não têm suporte:  
  
-   Os operadores compostos `+=`, `-=`, `%=`, `/=`, e `*=`  
  
-   Várias conversões, inclusive conversões numéricas e conversões de tipo de argumento  
  
-   Chamadas de método com mais de dois argumentos  
  
-   Getters da propriedade com mais de dois argumentos  
  
-   Setters de propriedade com argumentos  
  
-   Atribuição a um indexador  
  
-   Operadores boolianos `&&` e `||`  
  
### <a name="local-constants"></a>Constantes locais  
 As constantes locais não têm suporte.  
  
### <a name="import-aliases"></a>Aliases de importação  
 Não há suporte para aliases de importação.  
  
### <a name="variable-declarations"></a>Declarações de variável  
 Você não pode declarar novas variáveis explícitas nas janelas do depurador. No entanto, você pode atribuir novas variáveis implícitas dentro de **imediato** janela. Essas variáveis implícitas têm o escopo para a sessão de depuração e não estão acessíveis fora do depurador. Por exemplo, a instrução `o = 5` implicitamente cria uma nova variável `o` e atribuir o valor 5 a ela. Essas variáveis implícitas são do tipo **objeto** , a menos que o tipo possa ser inferido pelo depurador.  
  
### <a name="unsupported-keywords"></a>Palavras-chave sem suporte  
  
-   `AddressOf`  
  
-   `End`  
  
-   `Error`  
  
-   `Exit`  
  
-   `Goto`  
  
-   `On Error`  
  
-   `Resume`  
  
-   `Return`  
  
-   `Select/Case`  
  
-   `Stop`  
  
-   `SyncLock`  
  
-   `Throw`  
  
-   `Try/Catch/Finally`  
  
-   `With`  
  
-   Namespace ou módulo de nível de palavras-chave, como `End Sub` ou `Module`.  
  
## <a name="see-also"></a>Consulte também  
 [Especificadores de formato em C++](../debugger/format-specifiers-in-cpp.md)   
 [Operador de contexto (C++)](../debugger/context-operator-cpp.md)   
 [Especificadores de formato em c#](../debugger/format-specifiers-in-csharp.md)   
 [Pseudovariáveis](../debugger/pseudovariables.md)