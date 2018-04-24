---
title: Especifique o símbolo (. PDB) e arquivos de origem no depurador | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/05/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0a77ef00ee549006f9b4c6efb255c23543d6746
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Especifique o símbolo (. PDB) e arquivos de origem no depurador do Visual Studio
Um arquivo de banco de dados (. PDB) do programa, também chamado de arquivo de símbolo, mapeia os identificadores que você criar no código-fonte para classes, métodos e outro código para os identificadores que são usadas em executáveis compilados do seu projeto. O arquivo .pdb também mapeia as instruções no código-fonte para instruções de execução nos arquivos executáveis. O depurador usa essas informações para determinar os dois tipos principais de informações:

* Nome do número de arquivos e linhas de origem a ser exibida no IDE do Visual Studio
* Local do executável a ser interrompido em quando você definir um ponto de interrupção

Um arquivo de símbolo também contém o local original dos arquivos de origem e, opcionalmente, o local de um servidor de origem de onde os arquivos de origem podem ser recuperados.
  
> [!TIP]
> Se você quiser depurar código fora de seu código de origem do projeto, como código do Windows ou o código de terceiros chama seu projeto, você precisa especificar o local de. o PDB (e, opcionalmente, os arquivos de origem do código externo) e esses arquivos precisam corresponder exatamente a compilação de t ele executáveis.  
 
##  <a name="BKMK_Find_symbol___pdb__files"></a> Onde o depurador procura por arquivos de símbolo? 
  
1.  No local especificado dentro da DLL ou do arquivo executável.  
  
     (Por padrão, se você compilou uma DLL ou um arquivo executável no seu computador, o vinculador coloca o caminho completo e o nome do arquivo associado .pdb dentro da DLL ou do arquivo executável. O depurador verifica primeiro se o arquivo de símbolo existe no local especificado dentro da DLL ou do arquivo executável. Isso é útil porque você sempre tem os símbolos disponíveis para o código que compilou no seu computador.)  
  
2.  arquivos. PDB que estão presentes na mesma pasta que o arquivo executável ou DLL.

3. Todos os locais [especificado nas opções do depurador](#BKMK_Specify_symbol_locations_and_loading_behavior) para arquivos de símbolo. 
  
    * Em algumas pastas de cache de símbolo locais.  
  
    * Qualquer rede, internet, ou servidores de símbolos local e locais especificados, como o Microsoft symbol server (se habilitado). 

> [!NOTE]
> Antes do Visual Studio 2012, quando você depurado código gerenciado em um dispositivo remoto necessário para colocar os arquivos de símbolo no computador remoto. A partir do Visual Studio 2012, todos os arquivos de símbolo devem estar localizados no computador local ou em um local [especificado nas opções do depurador](#BKMK_Specify_symbol_locations_and_loading_behavior).  
  
##  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Por que os arquivos de símbolo preciso correspondam exatamente os arquivos executáveis?  
O depurador carregará apenas um arquivo .pdb para um arquivo executável que corresponde exatamente ao arquivo .pdb criado quando o executável foi compilado (isto é, o .pdb deve ser o original ou uma cópia do arquivo .pdb original). Como o compilador é otimizado para a velocidade de compilação, além de sua tarefa principal de criar um código correto e eficiente, o layout real de um executável pode ser alterado mesmo se o código em si não tiver sido alterado. Para obter mais informações, consulte [por que o Visual Studio requerem arquivos de símbolo do depurador para corresponder exatamente os arquivos binários que foram criados com?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)
  
##  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Configurar onde o depurador procura arquivos de símbolo e o comportamento de carregamento de símbolo
 Quando você depurar um projeto no IDE do Visual Studio, o depurador carrega automaticamente os arquivos de símbolos que estão localizados no diretório do projeto. Você pode especificar caminhos de pesquisa alternativa e servidores de símbolos para a Microsoft, Windows ou componentes de terceiros em **Ferramentas > Opções > Depuração > símbolos**. Você também pode especificar os módulos específicos que você deseja que o depurador para carregar automaticamente os símbolos para. E você pode alterar essas configurações manualmente quando estiver depurando ativamente.  
  
1.  No Visual Studio, abra o **Ferramentas > Opções > Depuração > símbolos** página.  
  
     ![Ferramentas &#45; opções &#45; depuração &#45; página símbolos](../debugger/media/dbg_tools_options_symbols.gif "DBG_Tools_Options_Symbols")  
  
2.  Escolha a pasta ![ferramentas&#47; opções&#47; depuração&#47;ícone da pasta símbolos](../debugger/media/dbg_tools_options_foldersicon.png "DBG_Tools_Options_FoldersIcon") ícone. Texto editável aparece no **símbolo locais de arquivo (. PDB)** caixa.  
  
3.  Digite o caminho do diretório ou a URL do servidor de símbolos ou local do símbolo. O preenchimento de instruções ajuda você a localizar o formato correto.

    Você pode usar **Ctrl + Up** e **Ctrl + Down** para alterar a ordem de carregamento para locais de símbolo. Pressione **F2** para editar uma URL ou caminho do diretório.
  
4.  Para melhorar o símbolo de desempenho do carregamento digite o caminho de um diretório local onde os símbolos podem ser copiados por servidores de símbolo no **símbolos neste diretório de Cache** caixa um diretório local símbolos podem ser copiados para.  
  
    > [!NOTE]
    >  Não coloque o cache de símbolo em uma pasta protegida (como a pasta C:\Windows ou uma de suas subpastas). Use uma pasta de leitura/gravação.  
  
### <a name="specify-symbol-loading-behavior"></a>Especificar o comportamento de carregamento de símbolos 
  
Você pode especificar os arquivos que você deseja carregar automaticamente a partir de **símbolo locais de arquivo (. PDB)** caixa locais quando você iniciar a depuração. Os arquivos de símbolo no diretório do projeto são sempre carregados.  
  
1.  Escolha **todos os módulos, a menos que excluído** carregar todos os símbolos para todos os módulos, exceto aquelas que você especifica quando você escolhe o **especifique excluídos módulos** link.  
  
2.  Escolha o **somente os módulos especificados** opção e, em seguida, escolha **especificar módulos** para listar os módulos de símbolos de arquivos que você deseja carregar automaticamente. Os arquivos de símbolo para outros módulos são ignorados.  
  
### <a name="specify-additional-symbol-options"></a>Especificar opções adicionais de símbolo 
  
Você também pode definir as opções a seguir sobre o **Ferramentas > Opções > Depuração > geral** página:  
  
**Carregar exportações de DLL (somente nativo)**  
  
Quando selecionada, carrega as tabelas de exportação de DLL. Informações simbólicas das tabelas de exportação de DLL podem ser úteis se você estiver trabalhando com mensagens do Windows, procedimentos do Windows (WindowProcs), objetos COM, ou marshaling, ou qualquer DLL para a qual você não tem símbolos. A leitura das informações de exportação de DLL gera certa sobrecarga. Desse modo, esse recurso é desativado por padrão.  
  
Para ver quais símbolos estão disponíveis na tabela de exportação de uma DLL, use `dumpbin /exports`. Os símbolos estão disponíveis para qualquer DLL de 32 bits do sistema. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Os nomes de função de tabelas de exportação de DLL podem aparecer truncados em qualquer outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, consulte [/exports dumpbin](/cpp/build/reference/dash-exports).  
  
###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Usar servidores de símbolos para localizar arquivos de símbolo não em sua máquina local  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode baixar arquivos de símbolo de depuração dos servidores de símbolo que implementam o protocolo symsrv. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6) e [as ferramentas de depuração para Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) são duas ferramentas que podem implementar servidores de símbolos. Especifique os servidores de símbolo para usar os VS **opções** caixa de diálogo.  
  
 Os servidores de símbolo que você pode usar incluem:  
  
 **Servidores de símbolos públicos da Microsoft**  
  
 Para depurar uma pane que ocorre durante uma chamada a uma DLL do sistema ou a uma biblioteca de terceiros, você normalmente precisará dos arquivos de sistema .pdb, que contêm símbolos de DLLs, EXEs e drivers de dispositivo do Windows. Você pode obter esses símbolos de servidores de símbolo públicos da Microsoft. Os servidores de símbolo públicos da Microsoft fornecem símbolos para sistemas operacionais Windows, além do MDAC, IIS, ISA e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para usar os servidores de símbolo da Microsoft, escolha **opções e configurações** no **depurar** menu e, em seguida, escolha **símbolos**. Selecione **servidores de símbolos da Microsoft**.  
  
 **Servidores de símbolo em uma rede interna ou em seu computador local**  
  
 Sua equipe ou empresa pode criar servidores de símbolo para seus próprios produtos e como um cache para símbolos de fontes externas. Você pode ter um servidor de símbolo no seu próprio computador. Você pode inserir o local dos servidores de símbolo como uma URL ou um caminho **depuração**/**símbolos** página dos VS **opção diálogo**.  
  
 **Servidores de símbolos de terceiros**  
  
 Provedores de terceiros de aplicativos e bibliotecas do Windows podem fornecer acesso ao servidor de símbolo na Internet. Você também insere a URL desses servidores de símbolo **depuração**/**símbolos** página,  
  
> [!NOTE]
>  Ao usar um servidor de símbolo que não seja um dos servidores de símbolo públicos da Microsoft, verifique se o servidor de símbolo e seu caminho são confiáveis. Como os arquivos de símbolo podem conter códigos executáveis arbitrários, você pode ser exposto às ameaças de segurança.  
  
###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Localizar e carregar símbolos durante a depuração  
 Sempre que o depurador estiver no modo de interrupção, você poderá carregar símbolos para um módulo que foi excluído anteriormente pelas opções de depurador ou que o compilador não pôde localizar. É possível carregar símbolos usando os menus de atalho das janelas Pilha de Chamadas, Módulos, Locais, Autos e de todas as janelas de Inspeção. Se o depurador for interrompido no código que não tenha arquivos de símbolo ou de origem disponíveis, será exibida uma janela de documento. Aqui você pode localizar informações sobre os arquivos ausentes e executar ações para encontrá-los e carregá-los.
  
 **Localizar símbolos com as páginas do documento sem símbolos carregados**  
  
 Há várias maneiras de o depurador ser interrompido em um código que não tenha símbolos disponíveis:  
  
1.  Entrando no código.  
  
2.  Sendo interrompido no código a partir de um ponto de interrupção ou exceção.  
  
3.  Alternando para outro thread.  
  
4.  Alterando o registro de ativação clicando duas vezes em um quadro na janela Pilha de Chamadas.  
  
 Quando um desses eventos ocorre, o depurador exibe o **sem símbolos carregados** página para ajudá-lo a encontrar e carregar os símbolos necessários.  
  
 ![Nenhuma página símbolos carregados](../debugger/media/dbg_nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
-   Para alterar os caminhos de pesquisa, escolha um caminho não selecionado ou **novo** e digite um novo caminho. Escolha **carregar** para os caminhos de pesquisa novamente e carregar o arquivo de símbolo se ele for encontrado.  
  
-   Escolha **procurar e localizar***nome executável***...**  para substituir as opções de símbolo e repetir os caminhos de pesquisa. O arquivo do símbolo será carregado, se for encontrado, ou um Explorador de Arquivos será exibido para que você selecione manualmente o arquivo de símbolo.  
  
-   Escolha **alterar configurações de símbolo...**  para exibir o **depuração** > **símbolos** página da caixa de diálogo Opções do VS.  
  
-   Escolha **Exibir desmontagem** para mostrar a desmontagem em uma nova janela de uma vez.  
  
-   Para mostrar sempre a desmontagem quando os arquivos de origem ou o símbolo não são localizados, escolha o **caixa de diálogo Opções** link e selecione **habilitar a depuração de nível de endereço** e **Mostrar desmontagem se fonte não disponível**.  
  
     ![Opções de &#47; depuração &#47; opções gerais de desmontagem](../debugger/media/dbg_options_general_disassembly_checkbox.png "DBG_Options_General_disassembly_checkbox")  
  
 **Alterar as opções de símbolo no menu de atalho**  
  
 No modo de interrupção, você pode localizar e carregar símbolos para itens que são exibidos nas janelas Pilha de Chamadas, Módulos, Locais, Autos e todas as janelas de Inspeção. Selecione um item na janela, abra o menu de atalho e escolha uma das seguintes opções:  
  
|Opção|Descrição|  
|------------|-----------------|  
|**Carregar símbolos**|Tenta carregar símbolos de locais especificados no **depuração**/**símbolos** página do **opções** caixa de diálogo. Se o arquivo de símbolo não puder ser encontrado, o Explorador de Arquivos será iniciado para que você possa especificar um novo local de pesquisa.|  
|**Informações de carga de símbolo**|Apresenta informações que mostram o local de um arquivo de símbolo carregado ou os locais que foram pesquisados se o depurador não puder localizar o arquivo.|  
|**Configurações de símbolo...**|Abre o **depuração**/**símbolos** página dos VS **opções** caixa de diálogo.|  
|**Sempre carregar automaticamente**|Adiciona o arquivo de símbolo à lista de arquivos que são automaticamente carregados pelo depurador.|  
  
###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Definir opções de compilador para arquivos de símbolo  
 Quando você compilar o projeto do IDE do VS e use o padrão de **depurar** configuração de compilação, o C++ e compiladores gerenciados criam os arquivos de símbolos apropriado para seu código. Também é possível definir opções de compilador na linha de comando para criar arquivos de símbolo.  
  
 **Opções do C++**  
  
 Um arquivo de banco de dados do programa (.pdb) contém informações de depuração e estado do projeto que permite a vinculação incremental de uma configuração de depuração do seu programa. Um arquivo. PDB é criado quando você cria com [/ZI ou /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) (para C/C++).  
  
 Em [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], o [/Fd](/cpp/build/reference/fd-program-database-file-name) opção nomeia o arquivo. PDB criado pelo compilador. Quando você cria um projeto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando os assistentes, o **/Fd** opção é definida para criar um arquivo. PDB chamado *projeto*. PDB.  
  
 Se você criar seu aplicativo C/C++ usando um makefile, e você especificar **/ZI** ou **/Zi** sem **/Fd**, você acabará com dois arquivos. PDB:  
  
-   VC*x*. PDB, onde *x* representa a versão do Visual C++, por exemplo VC11.pdb. Esse arquivo armazena todas as informações de depuração para arquivos OBJ individuais e reside no mesmo diretório que o makefile do projeto.  
  
-   PDB esse arquivo armazena todas as informações de depuração para o arquivo the.exe. No C/C++, ele reside no subdiretório \debug.  
  
 Cada vez que ele cria um arquivo OBJ, o compilador do C/C++ mescla informações da depuração no VC*x*. PDB. As informações inseridas incluem informações de tipo, mas não incluem informações de símbolo como definições de função. Portanto, mesmo se todos os arquivos de origem incluam arquivos de cabeçalho como \<Windows. h >, os typedefs daqueles cabeçalhos são armazenados apenas uma vez, em vez de em cada arquivo OBJ.  
  
 O vinculador cria project.pdb, que contém informações de depuração para o arquivo EXE do projeto. O arquivo PDB contém informações de depuração completas, incluindo protótipos de função, não apenas as informações encontradas em VC*x*. PDB. Ambos os arquivos .pdb permitem atualizações incrementais. O vinculador também insere o caminho no arquivo .pdb do arquivo .exe ou .dll que ele cria.  
  
 O depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa o caminho para o arquivo .pdb no arquivo EXE ou DLL para localizar o arquivo project.pdb. Se o depurador não é possível localizar o arquivo. PDB nesse local, ou se o caminho é inválido (por exemplo, se o projeto foi movido para outro computador), o depurador pesquisará o caminho que contém o EXE, os caminhos de símbolo especificado no **opções** caixa de diálogo (**depuração** pasta **símbolos** nó). O depurador não carregará um arquivo .pdb que não corresponde ao executável que está sendo depurado. Se o depurador não é possível localizar um arquivo. PDB, um **localizar símbolos** caixa de diálogo for exibida, que permite que você pesquise os símbolos ou adicionar mais locais para o caminho de pesquisa.  
  
 **Opções do .NET framework**  
  
 Um arquivo de banco de dados do programa (.pdb) contém informações de depuração e estado do projeto que permite a vinculação incremental de uma configuração de depuração do seu programa. Um arquivo. PDB é criado quando você cria com **/Debug**. Você pode criar aplicativos com **/Debug: full** ou **/Debug: pdbonly**. Compilando com **/Debug: full** gerará código depurável. Compilando com **/Debug: pdbonly** gera arquivos. PDB, mas não gera o `DebuggableAttribute` que informa que o compilador JIT que as informações de depuração estão disponíveis. Use **/Debug: pdbonly** se você deseja gerar os arquivos. PDB para uma compilação de versão que você não deseja ser depurado. Para obter mais informações, consulte [/debug (opções do compilador c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) ou [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
 O depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa o caminho para o arquivo .pdb no arquivo EXE ou DLL para localizar o arquivo project.pdb. Se o depurador não é possível localizar o arquivo. PDB nesse local, ou se o caminho é inválido, o depurador pesquisará o caminho que contém o arquivo EXE e, em seguida, os caminhos de símbolo especificado no **opções** caixa de diálogo. Esse caminho é geralmente o **depuração** pasta o **símbolos** nó. O depurador não carregará um arquivo .pdb que não corresponde ao arquivo executável que está sendo depurado. Se o depurador não é possível localizar um arquivo. PDB, um **localizar símbolos** caixa de diálogo for exibida, que permite que você pesquise os símbolos ou adicionar mais locais para o caminho de pesquisa.  
  
 **aplicativos da Web**  
  
 O arquivo de configuração do aplicativo (Web.config) deve ser definido para o modo de depuração. O modo de depuração faz com que o ASP.NET gere símbolos para arquivos gerados dinamicamente e permite que o depurador se anexe ao aplicativo ASP.NET. O Visual Studio define isso automaticamente quando você iniciar a depuração, se você criou o projeto do modelo de projetos Web.  
  
##  <a name="BKMK_Find_source_files"></a> Arquivos de origem  
  
###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Onde o depurador procura por arquivos de origem  
 O depurador procura arquivos de origem nos seguintes locais:  
  
1.  Em arquivos abertos no IDE da instância do Visual Studio que iniciou o depurador.  
  
2.  Arquivos da solução que está aberto na instância do Visual Studio.  
  
3.  Os diretórios que são especificados no **propriedades comuns**/**depurar arquivos de origem** página nas propriedades da solução. (No **Solution Explorer**, selecione o nó da solução, com o botão direito e selecione **propriedades**. )  
  
4.  Nas informações de origem do .pdb do módulo. Esse pode ser o local do arquivo de origem quando o módulo foi compilado ou pode ser um comando para um servidor de origem.  
  
###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Localizar e carregar arquivos de origem com as páginas não Source/No símbolos carregados  
 Quando o depurador interromperá a execução em um local onde o arquivo de origem não está disponível, ele exibirá o **nenhuma fonte carregada** ou **sem símbolos carregados** páginas que podem ajudá-lo a localizar o arquivo de origem. O **sem símbolos carregados** é exibida quando o depurador não é possível localizar um arquivo de símbolo (. PDB) para o arquivo executável para concluir a pesquisa. A página Nenhum Símbolo fornece opções para procurar o arquivo. Se o .pdb for encontrado depois que você executar uma das opções e se o depurador puder recuperar o arquivo de origem usando as informações no arquivo de símbolos, a origem será exibida. Caso contrário, um **nenhuma fonte carregada** aparecerá que descreve o problema. A página exibe links de opções que podem executar ações que podem resolver o problema.  
  
###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Adicionar caminhos de pesquisa do arquivo de origem para uma solução  
 Você pode especificar uma rede ou diretórios locais para procurar arquivos de origem.  
  
1.  Selecione a solução no Gerenciador de soluções e escolha **propriedades** no menu de atalho.  
  
2.  Sob o **propriedades comuns** nó, escolha **depurar arquivos de origem**.  
  
3.  Clique na pasta ![ferramentas&#47; opções&#47; depuração&#47;ícone da pasta símbolos](../debugger/media/dbg_tools_options_foldersicon.png "DBG_Tools_Options_FoldersIcon") ícone. Texto editável aparece no **diretórios que contêm o código-fonte** lista.  
  
4.  Adicione o caminho que deseja pesquisar.  
  
 Observe que somente o diretório especificado será pesquisado. Você deve adicionar entradas para todos os subdiretórios que deseja pesquisar.  
  
###  <a name="BKMK_Use_source_servers"></a> Usar servidores de origem  
 Quando não há nenhum código-fonte no computador local ou o arquivo .pdb não corresponde ao código-fonte, você pode usar o servidor de origem para ajudar na depuração de um aplicativo. O Servidor de Origem recebe solicitações de arquivos e retorna os arquivos reais. O Servidor de Origem é executado por meio de um arquivo DLL chamado srcsrv.dll. O Servidor de Origem lê o arquivo .pdb do aplicativo, que contém ponteiros para o repositório do código-fonte, bem como os comandos usados para recuperar o código-fonte do repositório. Você pode limitar quais comandos terão permissão para execução do arquivo .pdb, listando os comandos permitidos dentro de um arquivo denominado srcsrv.ini, que deve ser colocado no mesmo diretório que srcsrv.dll e devenv.exe.  
  
> [!IMPORTANT]
>  Os comandos arbitrários podem ser inseridos no arquivo .pdb do aplicativo, portanto, certifique-se de colocar somente aqueles que você deseja executar no arquivo srcsrv.ini. Qualquer tentativa de executar um comando que não esteja no arquivo srcsvr.ini fará com que uma caixa de diálogo de confirmação seja exibida. Para obter mais informações, consulte [aviso de segurança: depurador deve executar comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros do comando. Portanto, tenha cuidado com comandos confiáveis. Por exemplo, se você confiar no cmd.exe, um usuário mal-intencionado pode especificar parâmetros que tornariam o comando perigoso.  
  
 **Para habilitar o uso de um servidor de origem**  
  
1.  Você deve cumprir as medidas de segurança descritas na seção anterior.  
  
2.  No menu **Ferramentas**, escolha **Opções**.  
  
     A caixa de diálogo **Opções** é exibida.  
  
3.  No **depuração** nó, escolha **geral**.  
  
4.  Selecione o **habilitar o suporte do servidor de origem** caixa de seleção.  
  
     ![Habilitar opções de servidor de origem](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  
  
5.  (Opcional) Escolha as opções filho que você deseja.  
  
     Observe que tanto **permitir que o servidor de origem para assemblies de confiança parcial (somente gerenciado)** e **sempre executar comandos do servidor de origem não confiável sem avisar** pode aumentar os riscos de segurança discutidos acima.  
  
## <a name="see-also"></a>Consulte também  
[Noções básicas sobre arquivos de símbolo e configurações de símbolo do Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[Símbolo de remoto .NET ao carregar as alterações no Visual Studio 2012 e 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)