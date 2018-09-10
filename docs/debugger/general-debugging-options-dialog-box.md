---
title: Geral, depuração, caixa de diálogo de opções | Microsoft Docs
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
ms.openlocfilehash: e46301c84b1a9b27eed8cb6667b312ff73af2960
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280631"
---
# <a name="general-debugging-options-dialog-box"></a>Caixa de diálogo Geral, Depuração, Opções
O **Ferramentas > Opções > Depuração > geral** página permite que você defina as opções descritas neste artigo.

Se você precisar restaurar as configurações padrão, você pode fazer isso usando **ferramentas** > **importar e exportar configurações** > **redefinir todas as configurações**. Se você quiser redefinir um subconjunto de configurações, salve suas configurações na **Import and Export Settings Wizard** antes de fazer as alterações que você deseja testar, em seguida, importar as configurações salvas mais tarde.
  
**Perguntar antes de excluir todos os pontos de interrupção** requer a confirmação antes de concluir a **excluir todos os pontos de interrupção** comando.  
  
**Interromper todos os processos quando um processo for interrompido** interrompe simultaneamente todos os processos aos quais o depurador é anexado, quando ocorrer uma interrupção.  
  
**Interromper quando exceções cruzarem AppDomain ou limites gerenciados/nativos** na depuração gerenciada ou de modo misto, o common language runtime pode capturar exceções que cruzem os limites de domínio de aplicativo ou limites gerenciados/nativos quando o seguinte as condições forem verdadeiras:  
  
1\) quando o código nativo chama código gerenciado usando interoperabilidade COM e o código gerenciado gera uma exceção. Ver [Introdução à interoperabilidade COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) quando o código gerenciado em execução no domínio do aplicativo 1 chama o código gerenciado no domínio do aplicativo 2, e o código no domínio do aplicativo 2 gera uma exceção. Ver [programação com domínios do aplicativo](/dotnet/articles/framework/app-domains/index).  

3\) quando o código chama uma função por meio de reflexão e a função gerará uma exceção. Ver [reflexão](/dotnet/framework/reflection-and-codedom/reflection).  
  
Condição 2 e 3, a exceção é às vezes detectada pelo código gerenciado em `mscorlib` em vez do common language runtime. Esta opção não afeta a quebra em exceções capturadas por `mscorlib`.  
  
**Habilitar a depuração do nível de endereços** habilita recursos avançados para depuração no nível do endereço (a **desmontagem** janela, o **registra** janela e pontos de interrupção de endereço).  
  
- **Mostrar desmontagem se a fonte não está disponível** mostra automaticamente o **desmontagem** janela quando você tenta depurar o código para o qual fonte não está disponível.  
  
**Habilitar filtros de ponto de interrupção** permite que você defina filtros em pontos de interrupção para que elas afetarão apenas processos específicos, threads ou computadores.  
 
**Use o novo auxiliar de exceção** permite que o auxiliar de exceção (Visual Studio 2017) que substitui o Assistente de exceção.
  
> [!NOTE]
> Para código gerenciado, essa opção foi chamada anteriormente **habilitar o Assistente de exceção** . 
  
**Habilitar apenas meu código** o depurador exibe e as etapas no código do usuário ("meu código"), ignorando o código de sistema e outro código que é otimizado ou que não tem símbolos de depuração.

- **Avisar se não houver código de usuário na inicialização (somente gerenciado)** quando a depuração começa com o Just My Code ativado, esta opção advertirá se não houver nenhum código de usuário ("meu código"). 

**Habilitar o .NET Framework depuração da origem** permite que o depurador para percorrer o código-fonte do .NET Framework. Habilitar esta opção desativa automaticamente Apenas Meus Código dos símbolos do .NET Framework que serão baixados em um local do cache. Você pode alterar o local do cache na **opções** caixa de diálogo **depuração** categoria, **símbolos** página.  
  
**Depurar parcialmente propriedades e operadores (somente gerenciado)** impede que o depurador de depuração de propriedades e operadores no código gerenciado.  
  
**Habilitar a avaliação de propriedade e outras chamadas de função implícitas** chama de ativar a avaliação automática de propriedades e de função implícitas nas janelas de variáveis e os **QuickWatch** caixa de diálogo.  
  
- **Chamar a função de conversão de cadeia de caracteres em objetos nas janelas de variáveis (c# e JavaScript somente)** executa uma chamada de conversão de cadeia de caracteres implícita ao avaliar objetos nas janelas variáveis. O resultado é exibido como uma cadeia de caracteres em vez do nome de tipo. Aplica-se somente à depuração no código em C. Essa configuração pode ser substituída pelo atributo DebuggerDisplay (consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Habilitar o suporte do servidor de origem** informa o depurador do Visual Studio para obter os arquivos de origem de servidores de origem que implementam o SrcSrv (`srcsrv.dll`) protocolo. Team Foundation Server e as ferramentas de depuração para Windows são dois servidores de origem que implementam o protocolo. Para obter mais informações sobre a configuração de SrcSrv, consulte o [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) documentação. Além disso, consulte [especificar arquivos de símbolo (. PDB) e código-fonte](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Pois lendo *. PDB* arquivos pode executar código arbitrário em arquivos, certifique-se de que você confia no servidor.  
  
- **Imprimir mensagens de diagnóstico de servidor de origem para a janela de saída** ao suporte do servidor de origem está habilitado, essa configuração ativa ao diagnóstico.  
  
- **Permitir que o servidor de origem para os assemblies de confiança parcial (somente gerenciado)** ao suporte do servidor de origem está habilitado, essa configuração substitui o comportamento padrão de não recuperar as fontes para assemblies de confiança parcial.  

**Habilitar o suporte a Link de origem** informa o depurador do Visual Studio para baixar os arquivos de origem para os arquivos. PDB que contêm informações de Link de origem. Para obter mais informações sobre o Link de origem, consulte a [especificação de Link de origem](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Realçar a linha inteira para pontos de interrupção e a instrução atual (C++)** quando o depurador realça um ponto de interrupção ou a instrução atual, ele realça a linha inteira.  
  
**Exigir arquivos de origem correspondam exatamente à versão original** informa o depurador para verificar se um arquivo de origem corresponde a versão do código-fonte usado para criar o arquivo executável que você está depurando. Se não coincide com a versão, você será solicitado a encontrar uma origem correspondente. Se uma fonte compatível não for encontrada, o código-fonte não será exibido durante a depuração. 
  
**Redirecionar todo o texto da janela Saída para a janela imediata** envia todas as mensagens do depurador que normalmente apareceriam na **saída** janela para o **imediato** janela em vez disso.  
  
**Mostrar estrutura bruta de objetos nas janelas de variáveis** desativa todas as personalizações de exibição de estrutura de objeto. Para obter mais informações sobre personalizações de exibição, consulte [criar exibições personalizadas de objetos gerenciados](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Suprimir Otimização JIT no carregamento do módulo (somente gerenciado)** desabilita a otimização JIT de código gerenciado quando um módulo é carregado e JIT é compilado enquanto o depurador é anexado. Desativar a otimização pode facilitar a depuração de alguns problemas, embora às custas de desempenho. Se você estiver usando Apenas Meu Código, a supressão da otimização de JIT poderá fazer com que código que não seja do usuário apareça como código do usuário ("Meu Código"). Para obter mais informações, consulte [Otimização JIT e depuração](../debugger/jit-optimization-and-debugging.md).

**Habilitar a depuração de JavaScript para ASP.NET (Chrome e o IE)** permite que o depurador de script para aplicativos ASP.NET. No primeiro uso no Chrome, você precisa entrar no navegador no primeiro uso, para habilitar as extensões do Chrome que você instalou. Desabilite essa opção para reverter para o comportamento herdado.    

**Carregar exportações de dll** carrega as tabelas de exportação de dll. Informações de símbolo de tabelas de exportação de dll podem ser útil se você estiver trabalhando com mensagens do Windows, procedimentos do Windows (WindowProcs), objetos COM, ou marshaling ou qualquer dll para o qual você não tem símbolos. Informações de exportação lendo dll envolve alguma sobrecarga. Desse modo, esse recurso é desativado por padrão.  
  
Para ver quais símbolos estão disponíveis na tabela de exportação de uma dll, use `dumpbin /exports`. Símbolos estão disponíveis para qualquer dll do sistema de 32 bits. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Nomes de função de tabelas de exportação de dll podem aparecer truncados em outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, consulte [dumpbin/exportações](/cpp/build/reference/dash-exports).  
  
**Mostrar pilhas paralelas de baixo para cima de diagrama** controla a direção na qual as pilhas são exibidas na **pilhas paralelas** janela.
  
**Ignorar as exceções de acesso de memória GPU, se os dados gravados não tiver alterado o valor** ignora as condições de corrida que foram detectadas durante a depuração caso os dados não forem alterados. Para obter mais informações, consulte [depurando código de GPU](../debugger/debugging-gpu-code.md).  
  
**Use o modo de compatibilidade gerenciado** substitui o mecanismo com uma versão herdada para habilitar estes cenários de depuração padrão:  
  
- Você está usando uma linguagem .NET Framework diferente de C#, VB ou F#, que fornece seu próprio Avaliador de Expressão (incluindo C++/CLI).  
  
- Você deseja habilitar editar e continuar para projetos do C++ durante a depuração de modo misto.  
  
> [!NOTE]
> O modo escolhendo compatibilidade gerenciada desativa alguns recursos que são implementados somente no mecanismo de depuração padrão. 

**Use os avaliadores de expressão c# e VB herdados** o depurador usará os avaliadores de expressão do Visual Studio 2013 C# /VB em vez dos avaliadores de expressão baseada em Roslyn de 2015 do Visual Studio.    
  
**Avisar ao usar os visualizadores do depurador personalizados contra processos potencialmente inseguros (somente gerenciado)** Visual Studio avisa você quando você estiver usando um visualizador de depurador personalizada que está executando o código do processo de depuração, porque ele pode estar em execução não seguro código.  
  
**Habilitar alocador de heap de depuração do Windows (somente nativo)** permite que o heap de depuração do windows melhorar o diagnóstico de heap. Habilitar essa opção afetará o desempenho de depuração.  
  
**Habilitar ferramentas de depuração da interface do usuário para XAML** a Live Visual Tree e os windows Live propriedade explorar aparecerão quando você inicia a depuração (F5) um tipo de projeto com suporte. Para obter mais informações, consulte [propriedades de XAML de inspecionar durante a depuração](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Visualizar os elementos selecionados no Live Visual Tree** elemento XAML o cujo contexto é selecionado também está selecionado em de **Live Visual Tree** janela.  
  
- **Mostrar ferramentas de tempo de execução no aplicativo** mostra a **Live Visual Tree** comandos em uma barra de ferramentas na janela principal do aplicativo XAML que está sendo depurado. Essa opção foi introduzida no Visual Studio 2015 atualização 2. 

- **Habilitar o XAML Edit and Continue** lhe permite usar Editar e continuar o recurso para o código XAML. 
  
**Habilitar ferramentas de diagnóstico durante a depuração** as **ferramentas de diagnóstico** janela é exibida enquanto você está depurando.
  
**Mostrar tempo decorrido PerfTip durante a depuração** a janela de código exibe o tempo decorrido de uma chamada de método fornecido quando você estiver depurando.  
  
**Habilitar Editar e continuar** você pode usar o editar e continuar funcionalidade durante a depuração.  
  
- **Habilitar nativo de editar e continuar** você pode usar o editar e continuar funcionalidade durante a depuração de código C++ nativo. Para obter mais informações, consulte [editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Aplicar alterações ao continuar (somente nativo)** Visual Studio compila automaticamente e aplica as alterações de código pendentes feitas ao continuar o processo de um estado de interrupção. Se não estiver selecionada, você pode optar por aplicar alterações usando o item de "Aplicar alterações de código" no menu Depurar.  
  
- **Avisar sobre código obsoleto (somente nativo)** obter avisos sobre código obsoleto.    

**Mostrar execução clique de botão no editor durante a depuração** quando essa opção é selecionada, o [executar com um clique](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) botão será mostrado durante a depuração.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opções com suporte em versões mais antigas do Visual Studio

Se você estiver usando uma versão mais antiga do Visual Studio, algumas opções adicionais podem estar presentes.

**Habilitar o Assistente de exceção** para código gerenciado, habilitado o Assistente de exceção. No Visual Studio 2017, o auxiliar de exceção substituído o Assistente de exceção.

**Desenrolar a pilha de chamadas em exceções não tratadas** faz com que o **pilha de chamadas** janela para reverter a pilha de chamadas para o ponto antes da ocorrência de exceção sem tratamento. 

**Avisar se não houver símbolos na inicialização (somente nativo)** exibe uma caixa de diálogo de aviso quando você tenta depurar um programa para o qual o depurador não tem nenhuma informação de símbolo. 

**Avisar se a depuração de script estiver desabilitada na inicialização** exibe uma caixa de diálogo de aviso quando o depurador é iniciado com a depuração de script desabilitada.

**Usar o modo de compatibilidade nativa** quando essa opção é selecionada, o depurador usa o depurador nativo do Visual Studio 2010, em vez do novo depurador nativo.  
  
Você deve usar essa opção quando você estiver depurando o código C++ .NET, pois o novo mecanismo de depuração não dá suporte a expressões de avaliação C++ .NET. No entanto, a habilitação do modo de compatibilidade nativa desabilita muitos recursos que dependem da implementação atual do depurador para operar. Por exemplo, o mecanismo herdado não tem muitos visualizadores para tipos internos, como `std::string` em projetos do Visual Studio 2015.   Use os projetos do Visual Studio 2013 para a melhor experiência de depuração nesses casos.
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)
