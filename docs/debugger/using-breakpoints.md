---
title: "Usar pontos de interrupção no depurador do Visual Studio | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords: breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: "57"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e5873276795477778e4c358d59788248230bb4b5
ms.sourcegitcommit: 062795f922e7b59fe00d3d95a01a9a8a28840017
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Usar pontos de interrupção no depurador do Visual Studio
Você pode definir pontos de interrupção quando você deseja interromper a execução do depurador, talvez para ver o estado de variáveis de código ou para examinar a pilha de chamadas. Eles são uma das técnicas de depuração mais importantes na caixa de ferramentas do desenvolvedor.  
  
##  <a name="BKMK_Overview"></a>Definindo um ponto de interrupção no código-fonte  
 Você pode definir um ponto de interrupção no código-fonte clicando na margem esquerda de um arquivo de código fonte ou colocar o cursor em uma linha de código e pressionando F9. O ponto de interrupção aparece como um ponto vermelho na margem esquerda e a linha de código é colorida também:  
  
 ![Definir um ponto de interrupção](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Quando você executar esse código no depurador, execução é interrompida sempre que o ponto de interrupção é atingido, antes do código nessa linha é executado. A linha do código-fonte é colorida amarela:  
  
 ![Execução de ponto de interrupção interrompida](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 Neste ponto, o valor de `testInt` ainda é 1.  
  
 Você pode examinar o estado atual do aplicativo, incluindo os valores de variáveis e a pilha de chamadas. Para obter mais informações sobre a pilha de chamadas, consulte [como: usar a janela pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Você pode definir um ponto de interrupção em qualquer linha de código executável. Por exemplo, no c# código anteriormente, você pode definir um ponto de interrupção na declaração de variável, o `for` loop ou todo o código dentro do `for` loop, mas você não pode definir um ponto de interrupção as declarações de namespace ou classe ou a assinatura do método.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Configuração de outros tipos de pontos de interrupção  
 Você também pode definir pontos de interrupção na pilha de chamadas, na janela de desmontagem e, em código C++ nativo, em uma condição de dados ou um endereço de memória.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Definindo um ponto de interrupção na janela de pilha de chamadas  
 Você pode interromper a execução na instrução ou que retorna uma função de chamada, definindo um ponto de interrupção na linha de **pilha de chamadas** janela. Para obter mais informações sobre a pilha de chamadas, consulte [como: usar a janela pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md). O depurador deve ter parado em execução.  
  
1.  Iniciar a depuração do aplicativo, e espera execução é interrompida (por exemplo, em um ponto de interrupção). Abra o **pilha de chamadas** janela (**Depurar > Windows > pilha de chamadas**, ou **CTRL + ALT + C**).  
  
2.  A função de chamada e, em seguida, selecione **ponto de interrupção > Inserir ponto de interrupção**, ou usar apenas a tecla de atalho **F9**.  
  
3.  Um símbolo de ponto de interrupção aparece na margem esquerda da pilha de chamadas, ao lado do nome da chamada de função.  
  
 No **pontos de interrupção** janela, o ponto de interrupção de pilha de chamada aparece como um endereço com um local de memória que corresponde a próxima instrução executável na função. O depurador interrompe a execução na instrução.  
  
 Visualmente rastreamento pontos de interrupção durante a execução de código, consulte [mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Definindo um ponto de interrupção na janela de desmontagem  
 Para definir um ponto de interrupção em uma instrução de assembly, o depurador deve estar no modo de interrupção.  
  
1.  Iniciar a depuração do aplicativo, e espera execução é interrompida (por exemplo, em um ponto de interrupção). Abra o **desmontagem** janela (**Depurar > Windows > desmontagem**, ou **Ctrl + Alt + D**).  
  
2.  Clique na margem esquerda na instrução que você deseja interromper na ou defina o cursor na instrução e pressione **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Definindo um ponto de interrupção de dados (somente nativo C++)  
 Os pontos de interrupção interromper a execução quando um valor que é armazenado em um alterações de endereço de memória especificado. Se o valor é lido, mas não alterado, não interrompe a execução. Para definir pontos de interrupção de dados, o depurador deve estar em modo de interrupção.  
  
1.  Iniciar a depuração do aplicativo e aguarde até que um ponto de interrupção é atingido. No **depurar** menu, escolha **novo ponto de interrupção > ponto de interrupção de dados** (ou abrir o **pontos de interrupção** janela e escolha **Novo > ponto de interrupção de dados**.  
  
2.  No **endereço** , digite um endereço de memória ou uma expressão que é avaliada como um endereço de memória. Por exemplo, digite `&avar` para interromper quando o conteúdo da variável `avar` alterações.  
  
3.  No **contagem de bytes** lista suspensa, selecione o número de bytes que você deseja que o depurador para assistir. Por exemplo, se você selecionar **4**, o depurador observará os quatro bytes começando em `&avar` e quebrar se qualquer um dos bytes alterar o valor.  
  
 Tenha em mente que os pontos de interrupção de dados dependem da aplicabilidade de endereços específicos de memória.  
  
-   O endereço de uma variável é alterado de uma sessão de depuração para o próximo. Pontos de interrupção de dados serão desabilitados automaticamente no final de cada sessão de depuração.  
  
-   Se você definir um ponto de interrupção de dados em uma variável local, o permanece de ponto de interrupção habilitado quando a função termina, mas o endereço de memória não é mais aplicável, e o comportamento do ponto de interrupção é imprevisível. Se você definir um ponto de interrupção de dados em uma variável local, você deve remover ou desabilitar o ponto de interrupção antes do fim da função.  
  
 Pontos de interrupção não funcionam nestas condições:  
  
-   Um processo que está sendo depurado não grava o local de memória  
  
-   O local de memória é compartilhado entre dois ou mais processos  
  
-   O local de memória é atualizado dentro do kernel. Por exemplo, se a memória é passada para o Windows de 32 bits `ReadFile` função, a memória será atualizada de modo kernel e o depurador não interrompe a gravação de memória.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Definindo um ponto de interrupção com um endereço de memória (somente nativo C++)  
 Você também pode usar o endereço de um objeto para definir um ponto de interrupção em um método chamado em uma instância específica de uma classe.  Veja um exemplo:  
  
 Por exemplo, considerando um objeto do tipo `my_class` com o endereço, você pode definir um ponto de interrupção de função em um método chamado `my_method` chamado a partir dessa instância.  
  
1.  Defina um ponto de interrupção em algum lugar após essa instância da classe é instanciada.  
  
2.  Localizar o endereço da instância (digamos tem `0xcccccccc`).  
  
3.  Clique em **Depurar > Novo ponto de interrupção > ponto de interrupção de função** (ou **ALT + F9, B**).  
  
4.  Adicione o seguinte texto para o **nome da função** caixa:  
  
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Gerenciar pontos de interrupção  
 Você pode usar o **pontos de interrupção** janela (**Depurar > Windows > pontos de interrupção**, ou **CTRL + ALT + B**) para ver todos os pontos de interrupção que você tiver definido em sua solução:  
  
 ![Janela pontos de interrupção](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 O **pontos de interrupção** janela fornece um local central para gerenciar todos os seus pontos de interrupção, que pode ser especialmente útil em uma solução grande ou um cenário de depuração complexas em que os pontos de interrupção são essenciais. Se você precisar salvar ou compartilhar o estado e o local de um conjunto de pontos de interrupção, você pode exportar e importar os pontos de interrupção somente a partir de **pontos de interrupção** janela.  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Pontos de interrupção avançados  
  
## <a name="breakpoint-conditions"></a>Condições de ponto de interrupção  
 Você pode controlar quando e onde um ponto de interrupção executa definindo condições.  
  
1.  Clique com botão direito no ponto de interrupção ou passe o mouse sobre o ponto de interrupção e escolha o ícone de configurações.  
  
2.  No menu de contexto, selecione **condições**. Isso abre o **configurações de ponto de interrupção** janela:  
  
 ![Configurações de ponto de interrupção](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
 Quando você verificar o **condições** caixa, a janela se expande para mostrar os diferentes tipos de condições.  
  
 **Expressão condicional:** quando você seleciona a expressão condicional, você pode escolher duas condições: **é verdadeiro** e **quando alterado**. Escolha **é verdadeiro** se você quiser interromper quando a expressão é atendida, ou escolha **quando alterado** se você quiser interromper quando o valor da expressão for alterado.  
  
 No exemplo a seguir, vamos definir o ponto de interrupção atingido somente quando o valor de `testInt` é **4**:  
  
 ![Condição de ponto de interrupção é true](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
 No exemplo a seguir, vamos definir o ponto de interrupção atingido somente quando o valor de `testInt` alterações:  
  
 ![Ponto de interrupção quando alterado](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
 O comportamento de quando o campo alterado é diferente para diferentes linguagens de programação. Se você escolher **quando alterado** para código nativo, o depurador não considerará a primeira avaliação da condição para ser uma alteração, portanto, o ponto de interrupção não atingido na primeira avaliação. Se você escolher **quando alterado** para código gerenciado, o ponto de interrupção na primeira avaliação após **quando alterado** está selecionado.  
  
 Se você definir uma condição de ponto de interrupção com sintaxe inválida, será exibida uma mensagem de aviso. Se você especificar uma condição de ponto de interrupção com sintaxe válida mas semântica inválida, uma mensagem de aviso aparecerá na primeira vez em que o ponto de interrupção for atingido. Nos dois casos, o depurador interrompe a execução quando o ponto de interrupção inválido é atingido. O ponto de interrupção é ignorado somente se a condição é válida e avalia como `false`.  
  
 A condição pode ser qualquer expressão válida que seja reconhecida pelo depurador. Para obter mais informações sobre expressões válidas, consulte [expressões no depurador](../debugger/expressions-in-the-debugger.md).  

> [!NOTE]
> Você pode usar **CTRL + Enter** para fechar o **configurações de ponto de interrupção** janela.
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Usando IDs de objeto em condições de ponto de interrupção (c# e F #)  
 Há momentos em que você deseja observar o comportamento de um objeto específico; Por exemplo, você talvez queira descobrir por que um objeto foi inserido mais de uma vez em uma coleção. Em c# e F #, você pode criar IDs de objeto para instâncias específicas de [tipos de referência](/dotnet/csharp/language-reference/keywords/reference-types) e usá-los em condições de ponto de interrupção. A ID de objeto é gerada pelo common language runtime (CLR) serviços de depuração e associada ao objeto.  Para criar uma ID de objeto, faça o seguinte:  
  
1.  Defina um ponto de interrupção no código de algum tempo depois que o objeto foi criado.  
  
2.  Iniciar a depuração e quando a execução é interrompida no ponto de interrupção, localizar o ponto de interrupção a **locais** janela, clique duas vezes e selecione **Verifique a ID do objeto**.  
  
     Você deve ver uma  **$**  mais um número no **locais** janela. Este é o ID de objeto.  
  
3.  Adicione um novo ponto de interrupção condicional no ponto em que você deseja investigar, por exemplo quando o objeto está para ser adicionado à coleção.  
  
4.  Use a ID de objeto no campo expressão condicional. Por exemplo, se houver uma variável `item` que faz referência ao objeto que deve ser adicionado à coleção, você deve colocar **item = = $n**, onde  **n**  é o número de identificação do objeto.  
  
     A execução será interrompido no ponto quando o objeto está para ser adicionado à coleção.  
  
 Se você desejar excluir a ID de objeto, clique na variável de **locais** janela e selecione **excluir ID do objeto**.  
  
 Observe que as IDs de objeto criar referências fracas e não impede que o objeto que está sendo coletado como lixo. Eles só são válidos para a sessão de depuração atual.  
  
## <a name="hit-count"></a>Contagem de acertos  
 Se você suspeitar de que um loop em seu código inicia com comportamento inadequado após um certo número de iterações, você pode definir um ponto de interrupção para interromper a execução após um número especificado de ocorrências para a linha associada do código, em vez de ser forçado a pressionar repetidamente **F5**  para alcançar o nível de iteração.  
  
 No **configurações de ponto de interrupção** janela, defina a condição como **contagem de ocorrências**. Em seguida, você pode especificar o número de iterações. O exemplo a seguir, definimos o ponto de interrupção em todos os outros iteração de ocorrências:  
  
 ![Contagem de ocorrências de ponto de interrupção](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtro  
 Você pode restringir um ponto de interrupção seja acionado somente em dispositivos especificados ou em threads e processos especificados.  
  
 No **configuração de ponto de interrupção**janela, defina a condição como **filtro**. Insira uma ou mais das seguintes expressões.  
  
-   MachineName = "name"  
  
-   ProcessId = valor  
  
-   ProcessName = "name"  
  
-   ThreadId = valor  
  
-   ThreadName = "name"  
  
 Coloque os valores de cadeia de caracteres entre aspas duplas. Você pode combinar cláusulas usando `&` (AND) `||` (ou), `!` (NOT) e parênteses.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Pontos de rastreamento e as ações de ponto de interrupção  
 Um tracepoint é um ponto de interrupção que imprime uma mensagem na janela Saída. Um tracepoint pode funcionar como uma declaração de rastreamento temporária na linguagem de programação.  
  
 No **configurações de ponto de interrupção** janela, verifique o **ações** caixa. Escolha **registrar uma mensagem de janela de saída** no **ação** grupo. Você pode imprimir uma cadeia de caracteres genérica, como **este é um teste**. Para incluir o valor de uma variável ou expressão, coloque-o entre chaves.  
  
 Para interromper a execução quando o tracepoint é alcançado, desmarque o **continuar execução** caixa de seleção. Quando **continuar execução** estiver marcada, não a execução é suspensa. Nos dois casos, a mensagem é impressa.  
  
 Você pode usar as seguintes palavras-chave especiais no **mensagem**.  
  
|||  
|-|-|  
|**$ADDRESS**|Instrução atual|  
|**$CALLER**|Nome da função de chamada|  
|**$CALLSTACK**|Pilha de chamadas|  
|**$FUNCTION**|Nome da função atual|  
|**$PID**|id do processo|  
|**$PNAME**|Nome do processo|  
|**$TID**|id do thread|  
|**$TNAME**|Nome do thread|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Rótulos de ponto de interrupção  
 Rótulos de ponto de interrupção são usados somente no **pontos de interrupção** janela para classificar e filtrar a lista de pontos de interrupção. Para adicionar um rótulo para um ponto de interrupção, escolha a linha do ponto de interrupção e, em seguida, escolha **rótulo** no menu de contexto.  
  
## <a name="export-and-import-breakpoints"></a>Pontos de interrupção de importação e exportação  
 Você pode exportar um ponto de interrupção em um arquivo XML, clicando duas vezes no ponto de interrupção e selecionando **exportar**. O arquivo é salvo por padrão no diretório da solução. Para importar os pontos de interrupção, abra o **pontos de interrupção** janela (**CTRL + ALT + B**) e na barra de ferramentas, clique na seta para a direita (a dica de ferramenta é **importar pontos de interrupção de um arquivo**) .  
  
## <a name="see-also"></a>Consulte também  
[Solucionar problemas de pontos de interrupção no depurador do Visual Studio](../debugger/troubleshooting-breakpoints.md)  
[Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)
