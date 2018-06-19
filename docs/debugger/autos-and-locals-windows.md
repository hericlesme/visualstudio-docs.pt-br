---
title: Inspecionar variáveis nas janelas de locais e Autos | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3b19e8bd55320a9fbd5d8af037a9577db42a2fa
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454630"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows-in-visual-studio"></a>Inspecionar variáveis nos Autos e janelas de locais no Visual Studio
O **Autos** janela (durante a depuração, **CTRL + ALT + V, A**, ou **Depurar > Windows > Autos**) e o **locais** janela (durante a depuração **CTRL + ALT + V, L**, ou **Depurar > Windows > locais**) são muito úteis quando você deseja ver os valores de variáveis enquanto está depurando. O **locais** janela exibe as variáveis definidas no escopo local, que geralmente é a função ou método que está sendo executado atualmente. O **Autos** janela exibe variáveis usadas ao redor da linha atual (o local onde o depurador está parado). Exatamente quais variáveis são exibidos nessa janela são diferentes em idiomas diferentes. Consulte [o que as variáveis que aparecem na janela Autos?](#bkmk_whatvariables) abaixo.  
  
Se você precisar de mais informações sobre depuração básica, consulte [guia de Introdução com o depurador](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Examinando objetos na janela Autos e locais  
Matrizes e objetos são exibidos na janela Autos e locais, como controles de árvore. Clique na seta à esquerda do nome da variável para expandir a exibição para mostrar os campos e propriedades. Aqui está um exemplo de um [FileStream](/dotnet/api/system.io.filestream) objeto o **locais** janela:  
  
![Locals&#45;FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")  
  
## <a name="bkmk_whatvariables"></a> Quais variáveis são exibidos na janela Autos?  
 Você pode usar o **Autos** janela no código c#, Visual Basic e C++. O **Autos** não tem suporte JavaScript ou F #.  
  
 Em c# e Visual Basic, o **Autos** janela exibe qualquer variável usada na linha atual ou anterior. Por exemplo, se você declara quatro variáveis e defini-las da seguinte maneira:

```csharp
    public static void Main()
    {
       int a, b, c, d;
       a = 1;
       b = 2;
       c = 3;
       d = 4;
    }
```

 Se você definir um ponto de interrupção na linha `c = 3`; e executar o depurador, quando a execução é interrompida a **Autos** janela terá esta aparência:  

 ![Autos&#45;CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")  

 Observe que o valor de `c` é 0, porque a linha `c = 3` ainda não foi executada.  

 Em C++ o **Autos** janela exibe variáveis usadas pelo menos três linhas antes da linha atual (a linha na qual a execução é interrompida). Se você declarar seis variáveis:

```C++
    void main() {
        int a, b, c, d, e, f;
        a = 1;
        b = 2;
        c = 3;
        d = 4;
        e = 5;
        f = 6;
    }
```

 Se você definir um ponto de interrupção na linha `e = 5;` e executar o depurador, quando a execução é interrompida a **Autos** janela terá esta aparência:  
  
 ![Autos&#45;Cplus](../debugger/media/autos-cplus.png "Autos-Cplus")  
  
 Observe que a variável não foi inicializada porque o código na linha `e = 5;` ainda não foi executada.  
  
 Você também pode ver os valores de retorno de funções e métodos em determinadas circunstâncias. Consulte [ver os valores de retorno de chamadas de método](#bkmk_returnValue) abaixo.  
  
##  <a name="bkmk_returnValue"></a> Exibição de valores de retorno de chamadas de método  
 No código .NET e C++, você pode examinar valores de retorno quando você entra em ou fora de uma chamada de método. Essa funcionalidade é útil quando o resultado de uma chamada de método não é armazenado em uma variável local, por exemplo, quando um método é usado como um parâmetro ou valor de retorno de outro método.  
  
 O código c# a seguir adiciona os valores de retorno das duas funções:  

```csharp
static void Main(string[] args)  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    int x = sumVars(a, b) + subtractVars(c, d);  
}  
  
private static int sumVars(int i, int j)  
{  
    return i + j;  
}  
  
private static int subtractVars(int i, int j)  
{  
    return j - i;  
}  
```

 Defina um ponto de interrupção a `int x = sumVars(a, b) + subtractVars(c, d);` linha.  
  
 Iniciar a depuração e quando a execução é interrompida no primeiro ponto de interrupção, pressione **F10 (Step Over)**. Você deve ver o seguinte o **Autos** janela:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Por que são valores de variáveis, às vezes, vermelho no windows locais e Autos?  
Você pode perceber que o valor de uma variável, às vezes, é vermelho a **locais** e **Autos** windows. Esses são valores de variáveis que foram alterados desde a última avaliação. A alteração pode ser de uma sessão de depuração anterior, ou porque o valor foi alterado na janela.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Alterando o formato numérico de uma janela variável  
O formato numérico padrão é decimal, mas você pode alterá-la em hexadecimal. Clique dentro de um **locais** ou **Autos** janela e selecione **exibição Hexadecimal**. A alteração afeta todas as janelas do depurador.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Editar um valor em uma janela variável  
Você pode editar os valores de variáveis a maioria dos que aparecem no **Autos**, **locais**, **inspecionar**, e **QuickWatch** windows. Para obter informações sobre **inspecionar** e **QuickWatch** windows, consulte [inspeção e QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Clique duas vezes o valor que você deseja alterar e adicionar o novo o valor.  
  
Você pode inserir uma expressão para um valor, por exemplo `a + b`. O depurador aceita expressões de idioma mais válidas.  
  
Código C++ nativo, talvez você precise qualificar o contexto de um nome de variável. Para obter mais informações, consulte [o operador de contexto (C++)](../debugger/context-operator-cpp.md).  
 
No entanto, você deve ter cuidado ao alterar valores. Estes são alguns problemas possíveis:  
  
-   Avaliar algumas expressões pode alterar o valor de uma variável ou, de outra forma, afetar o estado do programa. Por exemplo, avaliar `var1 = ++var2` altera o valor de `var1` e `var2`.  
  
     Expressões que alteram os dados são chamadas [efeitos colaterais](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), que pode produzir resultados inesperados se você não estiver ciente delas. Certifique-se de que entender as consequências de uma alteração antes de você fazê-lo.  
  
-   Editar valores de ponto flutuante pode resultar em imprecisões secundárias devido à conversão decimal-binária de componentes fracionários. Mesmo uma edição aparentemente inofensiva pode resultar em alterações em alguns bits menos significativos na variável de ponto flutuante.  
  
## <a name="changing-the-window-context"></a>Alterar o contexto da janela  
Você pode usar o **local do depurador** barra de ferramentas para selecionar a função desejada, thread ou processo, que altera o contexto para as janelas de variáveis. Defina um ponto de interrupção e iniciar a depuração. (Se você não vir essa barra de ferramentas, você poderá habilitá-lo clicando em uma parte vazia da área de barra de ferramentas. Você deve ver uma lista de barras de ferramentas. Selecione **local do depurador**). Quando o ponto de interrupção é atingido, execução é interrompida e você pode ver a barra de ferramentas Depurar local, que é a linha inferior da ilustração a seguir.
  
![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")   
  
## <a name="see-also"></a>Consulte também  
 [Janelas do depurador](../debugger/debugger-windows.md)
