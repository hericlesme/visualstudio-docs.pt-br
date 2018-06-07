---
title: Geral, depuração, a caixa de diálogo Opções | Microsoft Docs
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b7af8c68764b3a9ed85bf6a52a3a6c4a0568203
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572044"
---
# <a name="general-debugging-options-dialog-box"></a>Caixa de diálogo Geral, Depuração, Opções
O **Ferramentas > Opções > Depuração > geral** página permite que você defina as opções descritas neste artigo.

Se você precisar restaurar as configurações padrão, você pode fazer essa usando **ferramentas** > **importar e exportar configurações** > **redefinir todas as configurações**. Se você quiser redefinir um subconjunto de configurações, salvar suas configurações no **Assistente de importação e exportação configurações** antes de fazer as alterações que você deseja testar, em seguida, importar as configurações salvas mais tarde.
  
**Perguntar antes de excluir todos os pontos de interrupção** requer confirmação antes de concluir o **excluir todos os pontos de interrupção** comando.  
  
**Interromper todos os processos quando um processo for interrompido** simultaneamente interrompe todos os processos aos quais o depurador é anexado, quando ocorrer uma interrupção.  
  
**Interromper quando exceções cruzarem AppDomain ou limites gerenciados/nativos** na depuração gerenciada ou de modo misto, o common language runtime pode capturar exceções que cruzam os limites de domínio de aplicativo ou limites gerenciados/nativos quando o seguinte condições são verdadeiras:  
  
1\) quando código nativo chama código gerenciado usando interoperabilidade COM, e o código gerenciado gera uma exceção. Consulte [Introdução à interoperabilidade COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) quando código gerenciado em execução no domínio do aplicativo 1 chama o código gerenciado no domínio do aplicativo 2, e o código de domínio do aplicativo 2 lançará uma exceção. Consulte [programação com domínios de aplicativo](/dotnet/articles/framework/app-domains/index).  

3\) quando o código chama uma função por meio de reflexão, e a função gera uma exceção. Consulte [reflexão](/dotnet/framework/reflection-and-codedom/reflection).  
  
Condição 2 e 3, a exceção às vezes é detectada pelo código gerenciado no `mscorlib` em vez do common language runtime. Esta opção não afeta a quebra em exceções capturadas por `mscorlib`.  
  
**Habilitar a depuração de nível de endereço** habilita recursos avançados para depuração no nível de endereço (a **desmontagem** janela, o **registra** janela e pontos de interrupção de endereço).  
  
- **Mostrar desmontagem se a fonte não está disponível** mostra automaticamente o **desmontagem** janela quando você tentar depurar o código fonte que não está disponível.  
  
**Habilitar filtros de ponto de interrupção** permite que você defina filtros em pontos de interrupção para que elas afetarão apenas processos específicos, threads ou computadores.  
 
**Use o novo auxiliar de exceção** permite que o auxiliar de exceção (Visual Studio 2017) que substitui o Assistente de exceção.
  
> [!NOTE]
> Para código gerenciado, esta opção foi chamada anteriormente **habilitar o Assistente de exceção** . 
  
**Habilitar apenas meu código** o depurador exibe e as etapas no código de usuário ("meu código"), ignorando o código do sistema e outro código que é otimizado ou que não têm símbolos de depuração.

- **Avisar se não houver código do usuário na inicialização (somente gerenciado)** quando a depuração iniciar com Just My Code ativado, essa opção avisa se não há nenhum código de usuário ("meu código"). 

**Habilitar o .NET Framework depuração da origem** permite que o depurador a depurar no código-fonte do .NET Framework. Habilitar esta opção desativa automaticamente Apenas Meus Código dos símbolos do .NET Framework que serão baixados em um local do cache. Você pode alterar o local do cache no **opções** caixa de diálogo, **depuração** categoria, **símbolos** página.  
  
**Percorrer propriedades e operadores (somente gerenciado)** impede que o depurador intervir propriedades e operadores em código gerenciado.  
  
**Habilitar avaliação de propriedades e outras chamadas de função implícitas** ativa avaliação automático das propriedades e da função implícita chama nas janelas de variáveis e o **QuickWatch** caixa de diálogo.  
  
- **Chamar a função de conversão de cadeia de caracteres em objetos nas janelas de variáveis (c# e JavaScript apenas)** executa uma chamada de conversão implícita de cadeia de caracteres ao avaliar os objetos nas janelas de variáveis. O resultado é exibido como uma cadeia de caracteres em vez do nome de tipo. Aplica-se somente à depuração no código em C. Essa configuração pode ser substituída pelo atributo DebuggerDisplay (consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Habilitar o suporte do servidor de origem** informa o depurador do Visual Studio para obter os arquivos de origem de servidores de origem que implementam o SrcSrv (`srcsrv.dll`) protocolo. Team Foundation Server e as ferramentas de depuração para Windows são dois servidores de origem que implementam o protocolo. Para obter mais informações sobre a instalação SrcSrv, consulte o [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) documentação. Além disso, consulte [especificar símbolo (. PDB) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Como ler arquivos .pdb pode executar o código arbitrário em arquivos, certifique-se de que você confia no servidor.  
  
- **Mensagens de diagnóstico de servidor de origem para a janela de saída de impressão** ao suporte do servidor de origem está habilitado, essa configuração é na exibição de diagnóstica.  
  
- **Permitir que o servidor de origem para assemblies de confiança parcial (somente gerenciado)** ao suporte do servidor de origem está habilitado, essa configuração substitui o comportamento padrão de não recuperar fontes para assemblies de confiança parcial.  

**Habilitar suporte a vínculo da fonte** informa o depurador do Visual Studio para baixar os arquivos de origem para os arquivos. PDB que contêm informações de Link de origem. Para obter mais informações sobre o Link de origem, consulte o [especificação de Link de origem](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Realce a linha inteira para pontos de interrupção e instrução atual (C++)** quando o depurador realça a um ponto de interrupção ou instrução atual, ele realça a linha inteira.  
  
**Requer arquivos de origem correspondam exatamente à versão original** informa o depurador para verificar se um arquivo de origem corresponde à versão do código-fonte usada para criar o executável que você está depurando. Se a versão não compatível, será solicitado que você encontrar uma origem correspondente. Se uma fonte compatível não for encontrada, o código-fonte não será exibido durante a depuração. 
  
**Redirecionar todo texto de janela de saída para a janela imediata** envia todas as mensagens que normalmente apareceriam do depurador de **saída** janela para o **imediato** janela em vez disso.  
  
**Mostrar estrutura bruta de objetos nas janelas de variáveis** desativa todas as personalizações de modo de exibição de estrutura de objeto. Para obter mais informações sobre personalizações de exibição, consulte [criar exibições personalizadas de objetos .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Suprimir Otimização JIT no carregamento do módulo (somente gerenciado)** desabilita a otimização JIT do código gerenciado quando um módulo é carregado e JIT é compilado, enquanto o depurador é anexado. Desativar a otimização pode facilitar a depuração de alguns problemas, embora às custas de desempenho. Se você estiver usando Apenas Meu Código, a supressão da otimização de JIT poderá fazer com que código que não seja do usuário apareça como código do usuário ("Meu Código"). Para obter mais informações, consulte [Otimização JIT e depuração](../debugger/jit-optimization-and-debugging.md).

**Habilitar depuração de JavaScript para o ASP.NET (Chrome e o IE)** permite que o depurador de script para aplicativos ASP.NET. No primeiro uso no Chrome, talvez seja necessário entrar no navegador no primeiro uso, para habilitar extensões de cromo que você instalou. Desabilite essa opção para reverter para o comportamento herdado.    

**Carregar exportações de dll** carrega as tabelas de exportação de dll. Informações de símbolo de tabelas de exportação de dll podem ser útil se você estiver trabalhando com mensagens do Windows, Windows procedimentos (WindowProcs), objetos COM, ou de empacotamento ou qualquer dll para o qual você não tem símbolos. Informações de exportação de dll de leitura envolve alguma sobrecarga. Desse modo, esse recurso é desativado por padrão.  
  
Para ver os símbolos que estão disponíveis na tabela de exportação de uma dll, use `dumpbin /exports`. Símbolos estão disponíveis para qualquer dll do sistema de 32 bits. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Nomes de função de tabelas de exportação de dll podem estar truncados em outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, consulte [/exports dumpbin](/cpp/build/reference/dash-exports).  
  
**Diagrama de baixo para cima de pilhas paralelas de apresentação de** controla a direção na qual as pilhas são exibidas no **pilhas paralelas** janela.
  
**Ignorar as exceções de acesso de memória GPU se os dados gravados não alteram o valor** ignora condições de corrida que foram detectadas durante a depuração se os dados não foram alterados. Para obter mais informações, consulte [depuração GPU código](../debugger/debugging-gpu-code.md).  
  
**Use o modo de compatibilidade gerenciado** substitui o padrão do mecanismo com uma versão herdada para habilitar esses cenários de depuração:  
  
- Você está usando uma linguagem .NET Framework diferente de C#, VB ou F#, que fornece seu próprio Avaliador de Expressão (incluindo C++/CLI).  
  
- Você deseja habilitar editar e continuar para projetos C++ durante a depuração de modo misto.  
  
> [!NOTE]
> O modo escolhendo compatibilidade gerenciado desativa alguns recursos que são implementados apenas no padrão do mecanismo de depuração. 

**Usar os avaliadores de expressão c# e VB herdados** o depurador usará os avaliadores de expressão do Visual Studio 2013 C# /VB em vez dos avaliadores de expressão com base em Roslyn de 2015 do Visual Studio.    
  
**Avisar ao usar visualizadores do depurador personalizados contra processos potencialmente inseguros (somente gerenciado)** Visual Studio avisa você quando você estiver usando um visualizador de depurador personalizada que está executando o código do processo de depuração, porque ele foi executado não seguro código.  
  
**Habilitar alocador de heap de depuração do Windows (somente nativo)** permite que o heap de depuração do windows melhorar o diagnóstico de heap. A habilitação dessa opção afetará o desempenho de depuração.  
  
**Habilitar as ferramentas de depuração da interface do usuário para XAML** a árvore Visual dinâmica e os windows Live propriedade explorar aparecerão quando você inicia a depuração (F5) um tipo de projeto com suporte. Para obter mais informações, consulte [propriedades inspecionar XAML durante a depuração](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Visualizar os elementos selecionados na árvore Visual** XAML o elemento cujo contexto está selecionado, também é selecionado no **árvore Visual dinâmica** janela.  
  
- **Mostrar ferramentas de tempo de execução no aplicativo** mostra o **árvore Visual dinâmica** comandos em uma barra de ferramentas na janela principal do aplicativo XAML que está sendo depurado. Essa opção foi introduzida no Visual Studio 2015 atualização 2. 

- **Habilitar XAML editar e continuar** permite usar Editar e continuar o recurso de código XAML. 
  
**Habilitar ferramentas de diagnóstico durante a depuração** o **ferramentas de diagnóstico** janela é exibida enquanto você está depurando.
  
**Mostrar o tempo decorrido de dica de desempenho durante a depuração** a janela de código exibe o tempo decorrido de uma chamada de método fornecido quando você está depurando.  
  
**Habilitar Editar e continuar** você pode usar o editar e continuar funcionalidade durante a depuração.  
  
- **Habilitar nativo editar e continuar** você pode usar o editar e continuar funcionalidade durante a depuração de código C++ nativo. Para obter mais informações, consulte [editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Aplicar alterações ao continuar (somente nativo)** Visual Studio compila automaticamente e aplica as alterações de código pendentes feitas ao continuar o processo de um estado de interrupção. Se não estiver selecionada, você pode optar por aplicar as alterações usando o item "Aplicar alterações de código" no menu Depurar.  
  
- **Avisar sobre código obsoleto (somente nativo)** receberá avisos sobre código obsoleto.    

**Mostrar execução clique de botão no editor durante a depuração** quando essa opção é selecionada, o [executar em, clique em](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) botão será mostrado durante a depuração.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opções de suporte em versões anteriores do Visual Studio

Se você estiver usando uma versão mais antiga do Visual Studio, algumas opções adicionais podem estar presentes.

**Habilitar o Assistente de exceção** para código gerenciado, habilitar o Assistente de exceção. No Visual Studio de 2017, o auxiliar de exceção substituído o Assistente de exceção.

**Desenrolar a pilha de chamadas em exceções não tratadas** faz com que o **pilha de chamadas** janela para reverter a pilha de chamadas para o ponto antes que a exceção não tratada ocorreu. 

**Avisar se nenhum símbolo na inicialização (somente nativo)** exibe uma caixa de diálogo de aviso quando você tentar depurar um programa para o qual o depurador não tem nenhuma informação de símbolo. 

**Avisar se a depuração de script está desabilitada na inicialização** exibe uma caixa de diálogo de aviso quando o depurador é iniciado com a depuração de script desabilitada.

**Use o modo de compatibilidade nativo** quando essa opção é selecionada, o depurador usa o depurador nativo do Visual Studio 2010, em vez do depurador nativo de novo.  
  
Você deve usar essa opção quando você estiver depurando o código C++ .NET, porque o novo mecanismo de depuração não oferece suporte para avaliadas expressões de C++ .NET. No entanto, habilitar o modo de compatibilidade nativo desabilita muitos recursos que dependem da implementação atual do depurador para operar. Por exemplo, o mecanismo herdado não tem muitos visualizadores para tipos internos, como `std::string` em projetos do Visual Studio 2015.   Use os projetos do Visual Studio 2013 para a melhor experiência de depuração nesses casos.
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
