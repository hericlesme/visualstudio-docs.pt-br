---
title: "Definir um observador variáveis no Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 04/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0f5c518becd09f6b94fb598975caa913d150ac2a
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Definir variáveis usando as janelas de QuickWatch no Visual Studio e observar um observador
Enquanto você está depurando, você pode usar o **inspecionar** e **QuickWatch** windows para inspecionar variáveis e expressões.  A diferença é que o **inspecionar** janela pode exibir várias variáveis, enquanto o **QuickWatch** janela exibe uma única variável ao mesmo tempo. 

Os windows estão disponíveis somente durante uma sessão de depuração. Para abrir o **inspecionar** janela, escolha **Depurar > Windows > Observação > Observação (1, 2, 3, 4)**). Para abrir o **QuickWatch** janela, ou com o botão direito na variável e escolha **QuickWatch** ou escolha **Depurar > QuickWatch**.
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Observando a uma única variável com QuickWatch  
 Você pode usar o **QuickWatch** janela para observar uma única variável. Por exemplo, se você tiver o seguinte código:  
  
```CSharp
static void Main(string[] args)  
{  
    int a, b;  
    a = 1;  
    b = 2;  
    for (int i = 0; i < 10; i++)  
    {  
        a = a + b;  
    }   
}  
```  
  
 Você pode observar uma variável na janela QuickWatch da seguinte maneira:  
  
1.  Defina um ponto de interrupção a `a = a + b;` linha.  
  
2.  Inicie a depuração. Interrompe a execução no ponto de interrupção.  
  
3.  Abra o **QuickWatch** janela (com o botão direito em `a`, em seguida, escolha **QuickWatch**, ou selecione `a` e pressione **SHIFT + F9**).

    Você deve ver uma variável no **valores** janela, com um valor de 1.

    ![Expressão QuickWatch](../debugger/media/watchexpression.png "QuickWatchExpression")  

    Se você deseja avaliar uma expressão usando a variável, adicione uma expressão como `a + b` para o **expressão** janela e clique em **reavaliar**. 
  
4.  Adicione a variável para o **inspecionar** janela de **QuickWatch** clicando **Adicionar inspeção**. 

    > [!NOTE]
    > O **QuickWatch** janela é uma janela de caixa de diálogo modal, para que você não pode continuar a depuração enquanto ele está aberto.  
  
5.  Fechar o **QuickWatch** janela. Agora você pode continuar a depuração enquanto você observar o valor de **inspecionar** janela.  
  
## <a name="observing-variables-with-the-watch-window"></a>Observando variáveis com a janela Inspeção  
 Você pode observar diversas variáveis com o **inspecionar** janela. Por exemplo, se você tiver o seguinte código:  
  
```C++  
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}
  
```  
  
 Adicione os valores das três variáveis à janela de inspeção da seguinte maneira:  
  
1.  Defina um ponto de interrupção a `c = a + b;` linha.  
  
2.  Iniciar a depuração (**F5**). Interrompe a execução no ponto de interrupção.  
  
3.  Abra a janela de inspeção (**Depurar > Windows > Observação > inspecionar 1**, ou **CTRL + ALT + W, 1**).  
  
4.  Adicionar o `a` variável para a primeira linha, o `b` variável para a segunda linha e o `c` variável para a terceira linha.

    Você pode adicionar variáveis clicando em uma linha vazia e digitar o nome da variável.
  
5.  Continuar a depuração (pressione **F11** para avançar o depurador).  
  
 Você deve ver os valores das variáveis mudando conforme você percorrer o `for` loop.  
  
 Se você estiver programando em código nativo, às vezes talvez seja necessário qualificar o contexto de um nome de variável ou de uma expressão que contenham um nome de variável. O contexto é a função, o arquivo de origem e o módulo onde uma variável está localizada. Se você tiver que qualificar o contexto, você pode usar a sintaxe do operador de contexto. Para obter mais informações, consulte [o operador de contexto (C++)](../debugger/context-operator-cpp.md).  
  
## <a name="observing-expressions-with-the-watch-window"></a>Observando expressões com a janela Inspeção  
 Agora vamos tentar usar uma expressão. Você pode adicionar qualquer expressão válida reconhecida pelo depurador.  
  
 Por exemplo, se você tiver o código listado na seção anterior, você pode obter a média dos valores a três assim:  
  
 ![Expressão de inspeção](../debugger/media/watchexpression.png "WatchExpression")  
  
 Em geral, as regras de avaliação de expressões no **inspecionar** janela são as mesmas regras para avaliar expressões na linguagem de codificação. Se a expressão tiver um erro de sintaxe, você pode esperar o mesmo erro de compilador que você veria no editor de códigos. Veja um exemplo:  
  
 ![Observe o erro de expressão](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a>Atualizando valores de inspeção estão desatualizados  
 Em determinadas circunstâncias, você verá um ícone de atualização (uma seta circular) quando uma expressão é avaliada no **inspecionar** janela.  Por exemplo, se você tiver desativada de avaliação de propriedade (**Ferramentas > Opções > Depuração > Habilitar avaliação de propriedades e outras chamadas de função implícitas**), e você tiver o código a seguir:  
  
```CSharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Se você definir um observador de `Count` propriedade da lista, você verá algo semelhante ao seguinte:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 A ilustração anterior mostra um erro ou um valor que está desatualizado. Geralmente você pode atualizar o valor clicando no ícone, mas em alguns casos você talvez prefira não para atualizá-lo. Primeiro, você precisa saber por que o valor não foi avaliado.  
  
 Se você apontar para o ícone, uma dica de ferramenta fornecerá informações sobre como a expressão não foi avaliada.  Se as setas de circundamento aparecerem, isso significará que a expressão não foi avaliada para um dos seguintes motivos:  
  
-   Ocorreu um erro porque a expressão estava sendo avaliada. Por exemplo, um tempo limite pode ter ocorrido, ou uma variável pode ter ficado fora do escopo.  
  
-   A expressão contém uma chamada de função, que pode disparar um efeito colateral do aplicativo (consulte [efeitos colaterais e expressões](#bkmk_sideEffects)).  
  
-   Avaliação automático das propriedades e chamadas de funções implícita pelo depurador está desativada (**Ferramentas > Opções > Depuração > Habilitar avaliação de propriedades e outras chamadas de função implícitas**), e, em seguida, a expressão não pode ser avaliado automaticamente.  
  
 Para atualizar o valor, clique no ícone de atualização ou pressione a barra de espaços. O depurador tenta reavaliar a expressão. Se o ícone de atualização foi exibida porque a avaliação automática de propriedades e outras chamadas de função implícita foi desativada, a expressão pode ser avaliada.  
  
 Se você vir um ícone que é um círculo com duas linhas onduladas semelhantes threads, a expressão foi avaliada não devido a uma possível dependência entre threads. Em outras palavras, a avaliar o código requer outros threads em seu aplicativo seja executado temporariamente. Quando você está no modo de interrupção, todos os threads em seu aplicativo normalmente estão parados. Permitir que outros threads executar temporariamente pode fazer com que inesperado afeta o estado do programa e faz com que o depurador ignore eventos como pontos de interrupção e as exceções geradas nesses threads.  
  
##  <a name="bkmk_sideEffects"></a>Efeitos colaterais e expressões  
 Avaliar algumas expressões pode alterar o valor de uma variável ou, de outra forma, afetar o estado do programa. Por exemplo, avaliar a expressão a seguir altera o valor de `var1`:  
  
```  
var1 = var2  
```  
  
 Esse código pode causar uma [efeito colateral](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efeitos colaterais podem dificultar depuração alterando o modo de que operação de seu programa.  
  
 Uma expressão que é conhecida por ter efeitos colaterais é avaliada apenas uma vez, quando você primeiro inseri-lo. As avaliações subsequentes serão desativadas. Manualmente, você pode substituir esse comportamento, clicando no ícone de atualização que aparece ao lado do valor.  
  
 Uma maneira de evitar todos os efeitos colaterais da é desativar a avaliação da função automática (**Ferramentas > Opções > Depuração > Habilitar avaliação de propriedades e outras chamadas de função implícitas**).  
  
 Quando a avaliação de propriedades ou chamadas de função implícita está desativada, você pode forçar a avaliação usando o **CA** modificador de formato (para c# somente). Consulte [Formatar especificadores em c#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="bkmk_objectIds"></a>Usando IDs de objeto da janela de inspeção (c# e Visual Basic)  

 Há momentos em que você deseja observar o comportamento de um objeto específico. Por exemplo, você talvez queira controlar um objeto referenciado por uma variável local depois que essa variável estiver fora do escopo. Em c# e Visual Basic, você pode criar IDs para instâncias específicas de tipos de referência de objeto e usá-los na janela Inspeção e em condições de ponto de interrupção. A ID de objeto é gerada pelo common language runtime (CLR) serviços de depuração e associada ao objeto.  
  
> [!NOTE]
>  IDs de objeto criar referências fracas e não impede que o objeto que está sendo coletado como lixo. Eles só são válidos para a sessão de depuração atual.  
  
 No código a seguir, um método cria um `Person` usando uma variável local, mas você deseja descobrir o que o `Person`do nome está em um método diferente:  
  
```CSharp  
class Person  
{  
    public Person(string name)  
    {  
        Name = name;  
    }  
    public string Name { get; set; }  
}  
  
public class Program  
{  
    List<Person> _people = new List<Person>();  
    public static void Main(string[] args)  
    {  
        MakePerson();  
        DoSomething();  
    }  
  
    private static void MakePerson()  
    {  
        var p = new Person("Bob");  
        _people.Add(p);  
    }  
  
    private static void DoSomething()  
    {  
        // more processing  
         Console.WriteLine("done");  
    }  
}  
  
```  
  
 Você pode adicionar uma referência ao `Person` objeto o **inspecionar** janela da seguinte maneira:  
  
1.  Defina um ponto de interrupção no código de algum tempo depois que o objeto foi criado.  
  
2.  Iniciar a depuração e quando a execução é interrompida no ponto de interrupção, localize a variável no **locais** janela, clique duas vezes e selecione **Verifique a ID do objeto**.  
  
3.  Você deve ver uma  **$**  mais um número no **locais** janela, que representa a ID de objeto.  
  
4.  Adicione a ID de objeto para a janela inspeção.  
  
5.  Defina um ponto de interrupção em que você deseja observar o comportamento do objeto.  No código anterior, que seria no `DoSomething()` método.  
  
6.  Continuar a depuração, e quando a execução é interrompida no `DoSomething()` método, o **inspecionar** janela exibe o `Person` objeto.  
  
> [!NOTE]
>  Se você deseja ver as propriedades do objeto, como `Person.Name` no exemplo acima, você deve ter habilitado avaliação da propriedade.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Usando os registros na janela de inspeção (C++)  
 Se você estiver depurando código nativo, você pode adicionar nomes de registro, bem como os nomes de variáveis usando  **$ \<registrar nome >** ou  **@ \<registrar nome >**.  Para obter mais informações, consulte [pseudovariáveis](../debugger/pseudovariables.md).  
  
## <a name="dynamic-view-and-the-watch-window"></a>Exibição dinâmica e a janela Inspeção  
 Algumas linguagens de script (por exemplo, Python ou JavaScript) usam dinâmico ou [digitação pato](https://en.wikipedia.org/wiki/Duck_typing), e linguagens .NET (na versão 4.0 e posterior) oferece suporte a objetos que são difíceis de observar usando as janelas de depuração normais, porque eles pode ter propriedades de tempo de execução e os métodos que não podem ser exibidos.  
  
 Quando a janela de observação exibe um objeto criado a partir de um tipo que implementa o [IDynamicMetaObjectProvider Interface](/dotnet/api/system.dynamic.idynamicmetaobjectprovider?view=netframework-4.7), o depurador adiciona um especial **exibição dinâmica** nó para o **Autos**  exibir. Esse nó mostra os membros dinâmicos do objeto dinâmico, mas não permite a edição dos valores de membro.  
  
 Se você clique qualquer filho de um **exibição dinâmica** e escolha **Adicionar inspeção**, o depurador insere uma nova variável de inspeção que converte um objeto para um objeto dinâmico. Em outras palavras, **nome do objeto** torna-se (**objeto (dinâmico)). Nome**.  
  
 Avaliando os membros de um **exibição dinâmica** pode ter efeitos colaterais. Para obter uma explicação dos quais são os efeitos colaterais, consulte [efeitos colaterais e expressões](#bkmk_sideEffects). Para c#, o depurador não automaticamente reavaliar os valores mostrados na **exibição dinâmica** quando você entrar em uma nova linha de código. Para o Visual Basic, expressões adicionados por meio de **exibição dinâmica** serão atualizados automaticamente.  
  
 Para obter instruções sobre como atualizar os valores de exibição dinâmica, consulte [valores de inspeção de atualização que estão desatualizados](#bkmk_refreshWatch).  
  
 Se você quiser exibir apenas a **exibição dinâmica** para um objeto, você pode usar o **dinâmico** especificador de formato:  
  
-   C#: **ObjectName, dinâmico**  
  
-   Visual Basic:: **$dynamic, ObjectName**  
  
 O **exibição dinâmica** também melhora a experiência de depuração para objetos COM. Quando o depurador encontra um objeto COM encapsulado em **ComObject**, ele adiciona um **exibição dinâmica** nó para o objeto.  
  
## <a name="see-also"></a>Consulte também  
 [Janelas do depurador](../debugger/debugger-windows.md)
