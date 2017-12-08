---
title: "Navegar por uma sessão de depuração no Visual Studio (Xaml e c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c69ff648e2a1ac8c60746f1e7879e80c2063c2a
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2017
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Navegar por uma sessão de depuração no Visual Studio (XAML e C#)
Este guia rápido demonstra como navegar sessões de depuração do Visual Studio e como exibir e alterar o estado do programa em uma sessão.  
  
 Este início rápido é para desenvolvedores que são novos para a depuração com o Visual Studio e a sessão de depuração para desenvolvedores que desejam saber mais sobre como navegar em um Visual Studio. Ele não ensina a arte de depurar a si próprio. Os métodos no código de exemplo destinam-se somente a demonstrar os procedimentos de depuração descritos neste tópico. Os métodos não utilizam as práticas recomendadas de design de aplicativo ou função. Na verdade, você rapidamente descobrirá que os métodos e o aplicativo em si, não muita coisa alguma.  
  
 As seções deste início rápido foram projetadas para serem o mais independentes possível, para que você pode ignorar qualquer seção que inclui informações que você já estiver familiarizado com. Você também não é necessárias para criar um aplicativo de exemplo; No entanto, recomendamos que ele e tornamos o processo o mais fácil possível.  
  
 **Atalhos de teclado do depurador.** A navegação pelo depurador Visual Studio é otimizada para o mouse e teclado. Muitas das etapas neste tópico incluem o acelerador de teclado ou a tecla de atalho em um comentário entre parênteses. Por exemplo, (teclado: F5) indica que pressionar a tecla F5 inicia ou continua a execução do depurador.  
  
## <a name="in-this-topic"></a>Neste tópico  
 Você pode aprender como:  
  
-   [Criar o aplicativo de exemplo](#BKMK_CreateTheApplication)  
  
-   [Definir e executar um ponto de interrupção, etapa em um método e examinar os dados de programa](#BKMK_StepInto)  
  
-   [Step-into, failover e fora de métodos](#BKMK_StepIntoOverOut)  
  
-   [Definir um ponto de interrupção condicional, executar até o cursor e visualizar uma variável](#BKMK_ConditionCursorVisualize)  
  
-   [Editar e continuar, recuperar de uma exceção](#BKMK_EditContinueRecoverExceptions)  
  
##  <a name="BKMK_CreateTheApplication"></a>Criar o aplicativo de exemplo  
 A depuração é focada em código, portanto o aplicativo de exemplo usa a estrutura do aplicativo UWP apenas para criar um arquivo de origem no qual você pode ver como funciona a navegação uma sessão de depuração e como examinar e alterar o estado do programa. Todo o código que você vai invocar é chamado a partir do construtor da página principal; controles não é adicionado e nenhum evento é tratado.  
  
 **Crie um aplicativo de UWP c# padrão.** Abra o Visual Studio. Na home page, escolha o **novo projeto** link. Na caixa de diálogo Novo projeto, escolha **Visual C#** no **instalado** lista e, em seguida, escolha **Windows Universal**. Na lista de modelos de projeto, escolha **(Universal do Windows) do aplicativo em branco**. Visual Studio cria uma nova solução e projeto e exibe o designer de MainPage. XAML e o editor de código XAML.  
  
 **Abra o arquivo de origem MainPage.xaml.cs.** Clique em qualquer lugar no editor do XAML e escolha **Exibir código**. O arquivo de code-behind MainPage.xaml.cs é exibido. Observe que apenas um método, o `MainPage()` construtor, está listado no arquivo.  
  
 **Substitua construtor MainPage com o código de exemplo.** Exclua o método MainPage(). Siga este link: [código de exemplo de navegação (Xaml e c#) do depurador](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/debugger/samples/debugger-navigation-sample-code-xaml-and-csharp.cs)e, em seguida, copie o código listado na seção c# para a área de transferência. (Escolha **novamente** no navegador ou do Visualizador da Ajuda para retornar a esta página de início rápido.) No editor do Visual Studio, cole o código no `partial class MainPage` bloco. Escolha CTRL + s para salvar o arquivo.  
  
 {1&gt;Agora você pode acompanhar os exemplos neste tópico.&lt;1}  
  
##  <a name="BKMK_StepInto"></a>Definir e executar um ponto de interrupção, etapa em um método e examinar os dados de programa  
 A maneira mais comum que você pode iniciar uma sessão de depuração é escolher **iniciar depuração** do **depurar** menu (teclado: F5). Execução inicia e continua até que um ponto de interrupção é atingido, você suspenda a execução manualmente, ocorra uma exceção ou o aplicativo seja encerrado.  
  
 Quando a execução é suspensa no depurador, você pode exibir o valor de uma variável ativa em uma dica de dados, passando o mouse sobre a variável. Você também pode abrir o windows locais e Autos para ver a lista de ativas variáveis e seus valores atuais. Adicionar uma ou mais variáveis para um permite que o janela Inspeção você concentre-se no valor das variáveis que o aplicativo continua a execução.  
  
 Depois que você suspenda a execução do aplicativo (que também é chamado de invadir o depurador), você pode controlar a maneira como o restante do código do programa é executado. Você pode continuar a linha por linha, movendo de uma chamada de método para o método em si, ou você pode executar um método chamado em uma única etapa. Esses procedimentos são chamados percorrendo o aplicativo. Você também pode retomar a execução padrão do aplicativo, executando até o próximo ponto de interrupção definido ou até a linha em que você posicionou o cursor. Você pode parar a sessão de depuração a qualquer momento. O depurador foi projetado para executar as operações de limpeza necessárias e sair da execução.  
  
### <a name="example-1"></a>Exemplo 1  
 Neste exemplo, defina um ponto de interrupção no construtor MainPage do arquivo MainPage.xaml.cs, passar o primeiro método, exibir valores de variáveis e parar a depuração.  
  
 **Defina um ponto de interrupção.** Definir um ponto de interrupção na instrução `methodTrack = "Main Page";` no construtor MainPage. Escolha a linha na medianiz sombreada do editor de código fonte (teclado: Posicione o cursor na linha e pressione a tecla F9).  
  
 ![Intervir](../debugger/media/dbg_basics_stepinto.png "DBG_Basics_StepInto")  
  
 O ícone de ponto de interrupção aparece na medianiz.  
  
 **Execute o ponto de interrupção.** Inicie a sessão de depuração escolhendo **iniciar depuração** no **depurar** menu (teclado: F5).  
  
 O aplicativo começa a executar e suspende a execução imediatamente antes da instrução em que você definir o ponto de interrupção. Ícone da linha atual na medianiz identifica o local e a instrução atual é realçada.  
  
 ![Definir um ponto de interrupção](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
 Você agora está no controle da execução do aplicativo e pode examinar o estado do programa percorrer as instruções do programa.  
  
 **Passar para o método.** Sobre o **depurar** menu, escolha **intervir** (teclado: F11).  
  
 ![Linha atual](../debugger/media/dbg_basics_currentline.png "DBG_Basics_CurrentLine")  
  
 Observe que o depurador se move para a próxima linha, que é uma chamada para o método de exemplo 1. Escolha entrar novamente. O depurador vai para o ponto de entrada do método de exemplo 1. Isso indica que o método foi carregado na pilha de chamadas e a memória para variáveis locais foram alocados.  
  
 {1&gt;Quando você entra em uma linha de código, o depurador executa uma das seguintes ações:&lt;1}  
  
-   {1&gt;Se a próxima instrução não for uma chamada para uma função em sua solução, o depurador executará a instrução, irá para a próxima instrução e suspenderá a execução.&lt;1}  
  
-   Se a instrução for uma chamada para uma função em sua solução, o depurador se move para o ponto de entrada da função chamada e então suspende a execução.  
  
 Continue entrar nas instruções de exemplo 1 até atingir o ponto de saída. O depurador realça a chave de fechamento do método.  
  
 **Examine os valores de variáveis em dicas de dados.** Quando você passar o mouse sobre um nome de variável, o nome, o valor e o tipo da variável é exibido em uma dica de dados.  
  
 ![Dica de dados do depurador](../debugger/media/dbg_basics_datatip.png "DBG_Basics_DataTip")  
  
 Passe o mouse sobre a variável `a`. Observe o tipo de dados de nome e valor. Passe o mouse sobre a variável `methodTrack`. Novamente, observe o tipo de dados de nome e valor.  
  
 **Examine os valores de variáveis na janela locais.** Sobre o **depurar** , aponte para **Windows**e, em seguida, escolha **locais**. (Teclado: Alt + 4).  
  
 ![Janela locais](../debugger/media/dbg_basics_localswindow.png "DBG_Basics_LocalsWindow")  
  
 A janela locais é uma exibição de árvore dos parâmetros e variáveis da função. As propriedades de uma variável de objeto são nós filho do objeto em si. O `this` variável é um parâmetro oculto em todos os métodos do objeto que representa o objeto em si. Nesse caso, ele representa a classe MainPage. Porque `methodTrack` é um membro de tipo de classe, seu valor e os dados MainPage são listados em uma linha abaixo `this`. Expanda o `this` nó para exibir o `methodTrack` informações.  
  
 **Adicione uma inspeção para a variável methodTrack.** O `methodWatch` variável é usada em todo este guia rápido para mostrar os métodos chamados nos exemplos. Para tornar mais fácil de exibir o valor da variável, adicione-a uma janela de observação. Clique no nome de variável na janela locais e, em seguida, escolha **Adicionar inspeção**.  
  
 ![Janela Inspecionar](../debugger/media/dbg_basics_watchwindow.png "DBG_Basics_WatchWindow")  
  
 Você pode inspecionar diversas variáveis em uma janela inspeção. Os valores de variáveis inspecionadas, como valores nas janelas de dica de dados e locais são atualizados sempre que a execução é suspensa. Você também pode adicionar variáveis à janela de inspeção de código no editor. Selecione a variável para assistir, com o botão direito e, em seguida, escolha **Adicionar inspeção**.  
  
##  <a name="BKMK_StepIntoOverOut"></a>Step-into, failover e fora de métodos  
 Em contraste a entrar em um método chamado por um método pai, passar sobre um método executa o método filho e então suspende a execução no método de chamada como o pai é retomada. Você pode passar por um método quando você estiver familiarizado com a maneira como o método funciona e tiver certeza de que sua execução não afetará o problema que você está investigando.  
  
 Passar sobre uma linha de código que não contém uma chamada de método executa a linha da mesma forma que entrar na linha.  
  
 Sair de um método filha continua a execução do método e então suspende a execução depois que o método retornará para seu método de chamada. Você pode sair de uma função longa quando tiver determinado que o restante da função não é significativo.  
  
 Tanto passar sobre quanto sair de uma função de executam a função.  
  
 ![Etapa em, sobre e sair de métodos](../debugger/media/dbg_basics_stepintooverout.png "DBG_Basics_StepIntoOverOut")  
  
### <a name="example-2"></a>Exemplo 2  
 Neste exemplo, você entrar, em e fora de métodos.  
  
 **Chame o método Example2 no construtor MainPage.** Edite o construtor MainPage e substitua a linha seguinte `methodTrack = String.Empty;` com `Example2();`.  
  
 ![Chamar o método Example2 do método demonstração](../debugger/media/dbg_basics_callexample2.png "DBG_Basics_CallExample2")  
  
 **Execute o ponto de interrupção.** Inicie a sessão de depuração escolhendo **iniciar depuração** no **depurar** menu (teclado: F5). O depurador suspende a execução no ponto de interrupção.  
  
 **Passe sobre a linha de código.** Sobre o **depurar** menu, escolha **passar por** (teclado: F10). O depurador executará a `methodTrack = "MainPage";` instrução da mesma maneira que entrar na instrução.  
  
 **Etapa em Example2 e Example2_A.** Pressione a tecla F11 para passar para o método de exemplo 2. Continuar entrar nas instruções Example2 até atingir a linha `int x = Example2_A();`. Intervir novamente, essa linha para mover para o ponto de entrada de Example2_A. Continue a entrar em cada instrução de Example2_A até retornar ao Example2.  
  
 ![Example2](../debugger/media/dbg_basics_example2.png "DBG_Basics_Example2")  
  
 **Passar por uma função.** Observe que a próxima linha em Example2, `int y = Example2_A();` é basicamente o mesmo que a linha anterior. Você pode passar sobre essa linha com segurança. Pressione a tecla F10 para mover a retomada de Example2 para essa segunda chamada para Example2_A. Escolha F10 para passar por esse método. Observe que o `methodTrack` cadeia de caracteres que indica o método Example2_A foi executado duas vezes. Você observará que o depurador se move imediatamente para a próxima linha. Ele não suspenda a execução em retoma o ponto Example2.  
  
 **Sair de uma função.** Escolha a tecla F11 para entrar no método Example2_B. Observe que não é muito diferente da Example2_A Example2_B. Para sair do método, escolha **sair** no **depurar** menu (teclado: Shift + F11). Observe que o `methodTrack` variável indica que Example2_B foi executado e que o depurador foi retornado para o ponto onde Example2 continua.  
  
 **Pare a depuração.** No menu Depurar, escolha parar depuração (teclado: Shift + F5). Isso encerra a sessão de depuração.  
  
##  <a name="BKMK_ConditionCursorVisualize"></a>Definir um ponto de interrupção condicional, executar até o cursor e visualizar uma variável  
 Um ponto de interrupção condicional Especifica uma condição que faz com que o depurador suspende a execução. A condição é especificada por uma expressão de código que pode ser avaliada como true ou false. Por exemplo, você pode usar um ponto de interrupção condicional para examinar o estado do programa em um método chamado com frequência somente quando uma variável atingir um determinado valor.  
  
 Executar até o cursor é como configurar um único ponto de interrupção. Quando a execução for suspensa, você poderá selecionar uma linha na origem e retomar a execução até que a linha selecionada seja atingida. Por exemplo, você pode percorrer um loop em um método e determinar que o código no loop está sendo executado corretamente. Em vez de percorrer cada iteração do loop, você pode executar até o cursor que é posicionado após o loop é executado.  
  
 Às vezes, é difícil ler um valor de variável na linha da dica de dados ou de janela variável. O depurador pode exibir cadeias de caracteres, HTML e Xml em um visualizador de texto que apresenta uma exibição formatada do valor em uma janela rolável.  
  
### <a name="example-3"></a>Exemplo 3:  
 Neste exemplo, você deve definir um ponto de interrupção condicional para quebrar em uma iteração específica de um loop, e então executar até o cursor é posicionado após o loop. Você também pode exibir o valor de uma variável em um visualizador de texto.  
  
 **Chame o método Example3 no construtor MainPage.** Edite o construtor MainPage e substitua a linha seguinte `methodTrack = String.Empty;` com a linha `Example3();`.  
  
 ![Chamar Example3 do método demonstração](../debugger/media/dbg_basics_callexample3.png "DBG_Basics_CallExample3")  
  
 **Execute o ponto de interrupção.** Inicie a sessão de depuração escolhendo **iniciar depuração** no **depurar** menu (teclado: F5). O depurador suspende a execução no ponto de interrupção no método MainPage.  
  
 **Etapa no método Example3.** Escolha **intervir** no **depurar** menu (teclado: F11) para mover para o ponto de entrada do método Example3. Continue entrando no método até ter iterado um ou dois loops do `for` bloco. Observe que ele levaria muito tempo para percorrer todas as 1.000 iterações.  
  
 **Defina um ponto de interrupção condicional.** Na medianiz esquerda da janela de código, clique na linha `x += i;` e, em seguida, escolha **condição**. Escolha o **condição** caixa de seleção e, em seguida, digite `i == 500;` na caixa de texto. Escolha o **é verdadeiro** opção e escolha **Okey**. O ponto de interrupção permite verificar o valor à 500ª iteração do loop `for`.  
  
 ![Caixa de diálogo de condição de ponto de interrupção](../debugger/media/dbg_basics_breakpointcondition.png "DBG_Basics_BreakpointCondition")  
  
 Você pode identificar um ícone de ponto de interrupção condicional pela sua cruz branca.  
  
 ![Ponto de interrupção condicional](../debugger/media/dbg_basics_conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")  
  
 **Execute o ponto de interrupção.** No menu Depurar, escolha continuar (teclado: F5). Na janela locais, confirme se o valor atual de `i` é 500. Observe que a variável `s` é representada como uma linha e é muito maior que a janela.  
  
 **Uma variável de cadeia de caracteres de Visual.** Clique no ícone de lupa no **valor** coluna o `s`.  
  
 A janela do Visualizador de texto é exibida e o valor da cadeia de caracteres é apresentado como uma cadeia de caracteres de várias linha.  
  
 **Execute até o cursor.** Clique na linha `methodTrack += "->Example3";` e, em seguida, escolha **executar até o Cursor** (teclado: mover o cursor para a linha; CTRL + F10). O depurador conclui as iterações do loop e então suspende a execução na linha de.  
  
 **Pare a depuração.** No menu Depurar, escolha parar depuração (teclado: Shift + F5). Isso encerra a sessão de depuração.  
  
##  <a name="BKMK_EditContinueRecoverExceptions"></a>Editar e continuar, recuperar de uma exceção  
 Em algumas circunstâncias, quando você dividir em código no depurador do Visual Studio, você terá a oportunidade para alterar o valor de variáveis e até mesmo as lógicas de instruções. Essa funcionalidade é chamado de editar e continuar.  
  
 Editar e continuar pode ser especialmente útil quando você interromper a uma exceção. Em vez de precisar parar e reiniciar a depuração de um procedimento longo e envolvido para evitar a exceção, você pode "Voltar" para a exceção para mover a execução para o ponto imediatamente antes que a exceção ocorreu e, em seguida, altere a variável incorreto ou a instrução e Continue com a sessão de depuração atual em um estado que não gerará uma exceção.  
  
 Embora você possa usar Editar e continuar em uma ampla variedade de situações, as condições específicas que não oferecem suporte a editar e continuar são difíceis especificar como as condições dependem da linguagem de programação, o estado atual da pilha de programa e o capacidade do depurador para alterar o estado sem corromper o processo. É a melhor maneira de determinar se uma alteração de edição é suportada apenas experimentá-lo; o depurador permite saber imediatamente se não há suporte para a alteração.  
  
### <a name="example-4"></a>Exemplo 4  
 Neste exemplo, você executar o depurador a uma exceção, rebobinar a exceção, corrija a lógica do método e, em seguida, altere o valor de uma variável para que você possa continuar a executar o método.  
  
 **Chame o método Example4 no construtor MainPage.** Edite o construtor MainPage() e substitua a linha seguinte `methodTrack = String.Empty;` com a linha `Example4();`.  
  
 ![Chamar Example4 do método demonstração](../debugger/media/dbg_basics_callexample4.png "DBG_Basics_CallExample4")  
  
 **Execute a exceção.** Inicie a sessão de depuração escolhendo **iniciar depuração** no **depurar** menu (teclado: F5). Pressione F5 novamente para continuar a execução. O depurador suspende a execução em que a exceção no método Example4 e exibe uma caixa de diálogo de exceção.  
  
 ![Caixa de diálogo de exceção](../debugger/media/dbg_basics_exceptiondlg.png "DBG_Basics_ExceptionDlg")  
  
 **Altere a lógica do programa.** É óbvio que o erro está no `if` condição: o valor de `x` deve ser alterada quando `x` é igual a 0; não quando `x` não é igual a zero. Escolha **quebra** para corrigir a lógica do método. Quando você tentar editar a linha, outra caixa de diálogo é exibida.  
  
 ![Caixa de diálogo Editar e continuar](../debugger/media/dbg_basics_editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")  
  
 Escolha **editar** e, em seguida, altere a linha `if (x != 0)` para `if (x == 0)`. O depurador persiste as alterações para a lógica de programa para o arquivo de origem.  
  
 **Altere o valor da variável.** Examinar o valor de `x` em uma dica de dados ou na janela locais. Ainda é 0 (zero). Se você tentar executar a instrução que provocou a exceção original, ela só irá gerar novamente. Você pode alterar o valor de `x`. Na janela locais, clique duas vezes o **valor** coluna o **x** linha. Altere o valor de 0 a 1.  
  
 ![Editar um valor na janela locais](../debugger/media/dbg_basics_editandcontinuefix.png "DBG_Basics_EditAndContinueFix")  
  
 Pressione a tecla F11 para passar para a instrução que iniciou anteriormente uma exceção. Observe que a linha é executado sem erro. Escolha F11 novamente.  
  
 **Pare a depuração.** Sobre o **depurar** menu, escolha **parar depuração** (teclado: Shift + F5). Isso encerra a sessão de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Iniciar uma sessão de depuração (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)   
 [Disparar suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)