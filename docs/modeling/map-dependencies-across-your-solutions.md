---
title: Mapear as dependências nas soluções
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 715d2a3778eaeee839f044b344c50302d3b66964
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="map-dependencies-across-your-solutions"></a>Mapear as dependências nas soluções

Quando você quiser entender as dependências em seu código, visualize-los Criando mapas de código. Isso ajuda você a ver como o código se ajusta sem ler nos arquivos e linhas de código.

![Exibir dependências nas soluções](../modeling/media/codemapsmainintro.png)

**Aqui estão alguns vídeos**:

- [Entender as dependências de código por meio de visualização](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)

- [Visualizar o impacto de uma alteração](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)

- [Noções básicas sobre código complexo com mapas de código](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understanding-complex-code-with-Code-Map-ENU)

## <a name="GetStarted"></a> Introdução ao mapa de códigos

**Usar mapas de código você será necessário**:

-   Visual Studio Enterprise: Crie mapas de código do editor de código, o Gerenciador de soluções, o modo de exibição de classe ou o Pesquisador de objetos.

-   Visual Studio Professional: Abrir mapas de código, faça edições limitadas e navegar pelo código.

> [!WARNING]
>  Antes de compartilhar mapas criados no Visual Studio Enterprise com outras pessoas que usam o Visual Studio Professional, certifique-se de que todos os itens do mapa (como itens ocultos, grupos expandidos e links entre grupos) ficam visíveis.

 **Você pode mapear as dependências para código nestes idiomas**:

-   Visual c# ou Visual Basic em uma solução ou assemblies (. dll ou .exe)

-   Código C ou C++ nativo ou gerenciado em projetos do Visual C++, arquivos de cabeçalho (. h ou `#include`) ou binários

-   Projetos e assemblies do X++ feitos com base nos módulos do .NET para Microsoft AX Dynamics

 **Observação:** para projetos que não seja o c# ou Visual Basic, há menos opções para iniciar um mapa de código ou adicionar itens a um mapa de código existente. Por exemplo, você não pode clique um objeto no editor de texto de um projeto de C++ e adicioná-lo a um mapa de código. No entanto, você pode arrastar e soltar elementos de código individuais ou arquivos de Gerenciador de soluções, modo de exibição de classe e Pesquisador de objetos.

### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Para ver as dependências gerais em sua solução

1.  Abra o **arquitetura** menu.

2.  Se você acabou de abrir a solução e ainda não tiver criado ou se seu código foi alterado desde a última vez que você criou, escolha **gerar mapa de código para solução**.

3.  Se seu código não foi alterado desde a última vez que você o criou, escolha **gerar mapa de código para solução sem compilação** para obter um desempenho mais rápido quando criar o mapa.

4.  [Consulte dependências gerais](#SeeOverviewSource) para entender como você pode usar mapas de código para exibir as dependências gerais em sua solução.

### <a name="to-see-specific-dependencies-within-your-solution"></a>Para ver as dependências específicas dentro de sua solução

1.  Com sua solução carregada, abra **Gerenciador de soluções**.

2.  Selecione todos os projetos, referências de assembly, pastas, arquivos, tipos ou membros que você deseja mapear.

3.  Sobre o **Gerenciador de soluções** barra de ferramentas, escolha **Mostrar no mapa de códigos**![criar novo gráfico selecionado nós botão de](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Ou abra o menu de atalho e escolha **Mostrar no mapa de códigos**. Você também pode arrastar itens da exibição de classe ou o Pesquisador de objetos em um novo ou um mapa de código existente.

4.  [Consulte dependências específicas](#SeeSpecificSource) para entender como você pode usar mapas de código para exibir as dependências específicas em sua solução.

###  <a name="CreateEmptyMap"></a> Para adicionar um novo mapa de código vazio à sua solução

1.  Em **Solution Explorer**, abra o menu de atalho para o nó da solução de nível superior. Escolha **adicionar** , em seguida, escolha **Novo Item**.

2.  Em **instalado**, escolha **geral**.

3.  No painel direito, escolha **documento gráfico direcionado** e, em seguida, escolha **adicionar**.

     Agora você tem um mapa em branco, que aparece em sua solução **itens de solução** pasta.

### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Para criar um novo mapa de código vazio sem adicioná-lo à sua solução

1.  Abra o **arquitetura** menu e escolha **novo mapa de código**.

     \- ou -

2.  Abra o **arquivo** menu e escolha **novo** , em seguida, escolha **arquivo**.

3.  Em **instalado**, escolha **geral**.

4.  No painel direito, escolha **documento gráfico direcionado** e, em seguida, escolha **abrir**.

     Agora você tem um mapa em branco, que não aparecem nas pastas da solução.

##  <a name="SeeOverviewSource"></a> Consulte dependências gerais

###  <a name="OverviewSource"></a> Ver as dependências em sua solução

1.  Sobre o **arquitetura** menu, escolha **gerar mapa de código para solução**.

     ![Gerar um comando de mapa](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")

     Você obtém um mapa que mostra os assemblies de nível superior e agregados links entre eles. Quanto maior o vínculo agregado, mais dependências ele representa.

2.  Use o **legenda** botão na barra de mapa de código para mostrar ou ocultar a lista de ícones de tipo de projeto (como teste, Web e projeto Phone), itens de código (como Classes, métodos e propriedades) e tipos de relação (como herda de Implementa e chamadas).

     ![Superior&#45;gráfico de dependência de nível de assemblies](../modeling/media/dependencygraph_toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")

     Esta solução de exemplo contém pastas de solução (**testes** e **componentes**), assemblies, projetos da Web e projetos de teste. Por padrão, todas as relações de confinamento aparecem como *grupos*, que você pode expandir e recolher. O **externos** grupo contiver qualquer coisa fora de sua solução, incluindo dependências de plataforma. Os assemblies externos mostram apenas os itens usados. Por padrão, os tipos de base do sistema estão ocultos no mapa para reduzir a desordem.

3.  Para analisar o mapa, expanda os grupos que representam os projetos e assemblies. Você pode expandir tudo pressionando **CTRL + A** para selecionar todos os nós e, em seguida, escolhendo **grupo**, **expandir** no menu de atalho.

     ![Expandir todos os grupos em um mapa de código](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")

4.  No entanto, isso não pode ser útil para uma solução grande. Na verdade, soluções complexas, as limitações de memória podem impedir que você expandir todos os grupos. Em vez disso, para ver dentro de um nó individual, expandi-lo. Mova o ponteiro do mouse sobre o nó e, em seguida, clique na divisa (seta para baixo) quando ele for exibido.

     ![Expandindo um nó em um mapa de código](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")

     Ou use o teclado selecionando o item e pressionando a tecla de mais (**+**). Para explorar níveis mais profundos do código, faça o mesmo para namespaces, tipos e membros.

    > [!TIP]
    >  Para obter mais detalhes de como trabalhar com o código de mapas usando o mouse, teclado e toque, consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

5.  Para simplificar o mapa e focar nas partes individuais, escolha **filtros** na barra de ferramentas de mapa de código e selecione apenas os tipos de nós e links que lhe interessam. Por exemplo, você pode ocultar todas as pastas de solução e Assembly recipientes.

     ![Simplificar o mapa filtrando contêineres](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")

     Você também pode simplificar o mapa, ocultando ou removendo grupos individuais e itens do mapa, sem afetar o código subjacente da solução.

6.  Para ver as relações entre itens, selecione-os no mapa. As cores dos links indicam os tipos de relação, como mostra o **legenda** painel.

     ![Exibir as dependências nas soluções](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

     Neste exemplo, os links roxos são chamadas, pontilhados links são referências e os links de azuis claras são acesso ao campo. Links verde pode ser herança, ou eles podem ser *agregar links* que indicam mais de um tipo de relação (ou *categoria*).

    > [!TIP]
    >  Se você vir um link verde, ele pode não significar que exista apenas uma relação de herança. Também podem ser chamadas de método, mas estão ocultas pela relação de herança. Para consultar tipos específicos de links, use as caixas de seleção no **filtros** painel para ocultar os tipos não estiver interessado em.

7.  Para obter mais informações sobre um item ou link, mova o ponteiro sobre ele até que uma dica de ferramenta é exibida. Mostra detalhes de um elemento de código ou as categorias que representa um link.

     ![Mostrar as categorias de uma relação](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")

8.  Para examinar os itens e dependências representadas por um link de agregação, primeiro selecione o link e, em seguida, abra o menu de atalho. Escolha **Mostrar Links participantes** (ou **Mostrar Links participantes no novo mapa de código**). Isso expande os grupos em ambas as extremidades do link e mostra somente os itens e as dependências que participam no link.

9. Para focar nas partes específicas do mapa, você pode continuar a remover itens que você não estiver interessado em. Por exemplo, para detalhar o modo de exibição de classe e de membro, simplesmente filtrar todos os nós no namespace de **filtros** painel.

     ![Busca detalhada em nível de classe e membro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png "DependencyGraph_ExpandedSelectedGroups_2012")

10. Outra maneira de foco em um mapa de solução complexa é gerar um novo mapa que contém os itens selecionados em um mapa existente. Manter **CTRL** enquanto seleciona os itens que você deseja se concentrar, abra o menu de atalho e escolha **novo gráfico da seleção**.

     ![Mostrar itens selecionados em um novo mapa de código](../modeling/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

11. O contexto de recipiente é transportado para o novo mapa. Ocultar pastas de solução e quaisquer outros contêineres que você não deseja ver usando o **filtros** painel.

     ![Os contêineres para simplificar a exibição de filtro](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")

12. Expanda os grupos e selecione os itens no mapa para exibir as relações.

     ![Selecionar itens para exibir as relações](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")

 Confira também: 

-   [Procurar e reorganizar mapas de códigos](../modeling/browse-and-rearrange-code-maps.md)

-   [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

-   Encontrar possíveis problemas em seu código por [executando um analisador](../modeling/find-potential-problems-using-code-map-analyzers.md).

###  <a name="OverviewCompiled"></a> Ver as dependências em assemblies ou binários

1.  [Criar um mapa de código vazio](#GetStarted), ou abrir um mapa de código existente (arquivo .dgml).

2.  Arraste os assemblies ou binários que você deseja mapear de fora do Visual Studio para o mapa. Por exemplo, arraste os assemblies ou binários do Windows Explorer ou do Explorador de arquivos.

> [!NOTE]
>  Você pode arrastar assemblies ou binários do Windows Explorer ou do Explorador de arquivos somente se você estiver executando no mesmo nível de permissões de controle de acesso de usuário (UAC) ele e o Visual Studio. Por exemplo, se o UAC estiver ativado e você estiver executando o Visual Studio como administrador, o Windows Explorer ou do Explorador de arquivos bloqueará a operação de arrastar. Para resolver esse problema, certifique-se de que ambas estão em execução com o mesmo nível de permissão ou desativar o UAC.

##  <a name="SeeSpecificSource"></a> Consulte dependências específicas
 Por exemplo, suponha que você tem uma revisão de código para executar em alguns arquivos com alterações pendentes. Para ver as dependências nessas alterações, você pode criar um mapa de código desses arquivos.

 ![Mostrar dependências específicas em um mapa de código](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

### <a name="see-specific-dependencies-in-your-solution"></a>Consulte as dependências específicas na solução

1.  Abra **Gerenciador de soluções**. Selecione os projetos, referências do assembly, pastas, arquivos, tipos e membros de seu interesse. Para localizar itens que têm dependências em tipos ou membros, abra o tipo ou o menu de atalho do membro do **Gerenciador de soluções**. Escolha o tipo de dependência e, em seguida, selecione os resultados.

2.  Mapear itens e seus membros. Sobre o **Gerenciador de soluções** clique da barra de ferramentas **Mostrar no mapa de códigos**![criar novo gráfico selecionado nós botão de](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").

     ![Selecione os itens que você deseja mapear](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")

3.  O mapa mostra os itens selecionados dentro de seus assemblies que contêm.

     ![Itens mostrados como grupos no mapa selecionado](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")

     Você também pode arrastar itens do Gerenciador de soluções, modo de exibição de classe, ou o Pesquisador de objetos para um espaço em branco ou um mapa de código existente. Para criar um mapa em branco, consulte [criar um mapa de código vazio](#GetStarted). Para incluir a hierarquia pai para os itens, pressione e segure o **CTRL** pressionada enquanto você arrasta os itens ou usar o **incluem pais** botão na barra de mapa de código para especificar a ação padrão.

    > [!NOTE]
    >  Quando você adicionar itens de um projeto compartilhado entre vários aplicativos, como Windows Phone ou Windows Store, esses itens são exibidos no mapa com o projeto de aplicativo ativo no momento. Se você alterar o contexto para outro projeto de aplicativo e adicionar mais itens do projeto compartilhado, esses itens agora serão exibidos com o projeto de aplicativo recém-ativo. Operações realizadas com um item no mapa se aplicam apenas aos itens que compartilham o mesmo contexto.

4.  Para explorar itens, expanda-os. Mova o ponteiro do mouse sobre um item e clique no ícone de divisa (seta para baixo) quando ele for exibido.

     ![Expandindo um nó em um mapa de código](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")

     Para expandir todos os itens, selecione-os usando **CTRL + A**, em seguida, abra o menu de atalho para o mapa e escolha **grupo**, **expandir**. No entanto, essa opção não estará disponível se expandir todos os grupos cria um mapa inutilizável ou problemas de memória.

5.  Continue a expandir itens que você está interessado, chegando até o nível de classe e de membro, se necessário.

     ![Expanda grupos de nível de classe e membro](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")

     Para ver os membros no código, mas não são exibidos no mapa, clique o **filhos buscar novamente** ícone ![buscar novamente filhos ícone](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") na parte superior esquerda de um grupo.

6.  Para ver mais itens relacionados no mapa, selecione um e escolha **Mostrar relacionados** na barra de ferramentas de mapa de código, selecione o tipo de itens relacionados para adicionar ao mapa. Como alternativa, selecione um ou mais itens, abra o menu de atalho e escolha o **Mostrar...**  opção para o tipo de itens relacionados para adicionar ao mapa. Por exemplo:

     Para uma **assembly**, escolha:

    |||
    |-|-|
    |**Mostrar Assemblies referenciados por este**|Adicione assemblies a que este assembly faz referência. Assemblies externos aparecem no **externos** grupo.|
    |**Mostrar Assemblies que fazem referência a este**|Adicione assemblies na solução que fazem referência a este assembly.|

     Para uma **namespace**, escolha **Mostrar Assembly contendo**, se não estiver visível.

     Para uma **classe** ou **interface**, escolha:

    |||
    |-|-|
    |**Mostrar Tipos Base**|Para obter uma classe, adicione a classe base e as interfaces implementadas.<br /><br /> Para obter uma interface, adicione as interfaces de base.|
    |**Mostrar Tipos Derivados**|Para obter uma classe, adicione as classes derivadas.<br /><br /> Para obter uma interface, adicione as interfaces derivadas e as classes de implementação ou structs.|
    |**Mostrar tipos referenciados por este**|Adicione todas as classes e os membros que essa classe usa.|
    |**Mostrar tipos que fazem referência a este**|Adicione todas as classes e seus membros que usam essa classe.|
    |**Mostrar que contém o Namespace**|Adicione o namespace pai.|
    |**Mostrar o Assembly e o Namespace que contém**|Adicione a hierarquia do contêiner pai.|
    |**Mostrar todos os tipos Base**|Adicione a classe base ou a hierarquia de interface recursivamente.|
    |**Mostrar todos os tipos derivados**|Para obter uma classe, adicione todas as classes derivadas recursivamente.<br /><br /> Para obter uma interface, adicione todas as interfaces derivadas e as classes de implementação ou structs recursivamente.|

     Para uma **método**, escolha:

    |||
    |-|-|
    |**Mostrar métodos chamados por este**|Adicione métodos que esse método chama.|
    |**Mostrar campos referenciados por este**|Adicione campos a que este método faz referência.|
    |**Mostrar contendo tipo**|Adicione o tipo de pai.|
    |**Mostrar contendo tipo, Namespace e Assembly**|Adicione a hierarquia do contêiner pai.|
    |**Mostrar métodos substituídos**|Para obter um método que substitui outros métodos ou implementa o método de uma interface, adicione todos os métodos abstratos ou virtuais em classes base que sejam substituídas e, se houver algum, o método da interface implementado.|

     Para uma **campo** ou **propriedade**, escolha:

    |||
    |-|-|
    |**Mostrar contendo tipo**|Adicione o tipo de pai.|
    |**Mostrar contendo tipo, Namespace e Assembly**|Adicione a hierarquia do contêiner pai.|

     ![Mostrar métodos chamados por este membro](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")

7.  O mapa mostra as relações. Neste exemplo, os métodos chamados `Find` método e sua localização na solução ou externamente.

     ![Mostrar dependências específicas em um mapa de código](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")

8.  Para simplificar o mapa e focar nas partes individuais, escolha **filtros** na barra de ferramentas de mapa de código e selecione apenas os tipos de nós e links que lhe interessam. Por exemplo, desative a exibição de pastas de solução, Assemblies e Namespaces.

     ![Use o painel de filtro para simplificar a exibição](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")

##  <a name="SeeSourceHeader"></a> Consulte as dependências entre os arquivos de origem C e C++ e arquivos de cabeçalho
 Se você quiser criar mapas mais completos para projetos C++, defina a opção de compilador de informações de procura (**/FR**) nesses projetos. Do contrário, uma mensagem é exibida e solicita a definição dessa opção. Se você selecionar **Okey**, define a opção do mapa atual. Você pode optar por ocultar a mensagem para todos os mapas posteriores. Se você ocultar essa mensagem, poderá exibi-la novamente. Defina a seguinte chave do registro `0` ou excluir a chave:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider: AutoEnableSbr**

 Quando você abre uma solução que contém projetos do Visual C++, pode demorar algum tempo para atualizar o banco de dados do IntelliSense. Durante esse tempo, você não poderá criar mapas de código de cabeçalho (. h ou `#include`) arquivos até que o banco de dados do IntelliSense conclui a atualização. É possível monitorar o andamento da atualização na barra de status do Visual Studio. Para resolver problemas ou mensagens exibidas porque algumas configurações do IntelliSense estão desabilitadas, consulte [solucionar problemas de mapas de código C e C++](#Troubleshooting).

-   Para ver as dependências entre todos os arquivos de origem e arquivos de cabeçalho em sua solução, o **arquitetura** menu, escolha **gerar gráfico de arquivos de inclusão**.

     ![Gráfico de dependência para código nativo](../modeling/media/dependencygraphgeneral_nativecode.png "DependencyGraphGeneral_NativeCode")

-   Para ver as dependências entre os arquivos abertos atualmente, os arquivos de origem relacionados e os arquivos de cabeçalho, abra o arquivo de origem ou o arquivo de cabeçalho. Abra o menu de atalho do arquivo em qualquer lugar dentro do arquivo. Escolha **gerar o gráfico de inclusão de arquivos**.

     ![Primeiro&#45;gráfico de dependência de nível de arquivo. h](../modeling/media/dependencygraph_native_firstlevel.png "DependencyGraph_Native_FirstLevel")

###  <a name="Troubleshooting"></a> Solucionar problemas de mapas de código C e C++
 Esses itens não são suportados para os códigos C e C++:

-   Tipos de base não são exibidos em mapas que incluem a hierarquia pai.

-   A maioria dos **Mostrar** itens de menu não estão disponíveis para o código C e C++.

 Esses problemas podem ocorrer quando você criar mapas de código para código C e C++:

|**Problema**|**Causa possível**|**Resolução**|
|---------------|------------------------|--------------------|
|O mapa de código falha ao gerar.|Nenhum projeto na solução foi compilado com êxito.|Corrija os erros de compilação ocorrem e, em seguida, gerar o mapa.|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deixar de responder quando você tenta gerar um mapa de código do **arquitetura** menu.|O arquivo de banco de dados do programa (.pdb) pode estar corrompido.<br /><br /> Um arquivo .pdb armazena informações de depuração, como o tipo, o método e as informações do arquivo de origem.|Recompile a solução e, em seguida, tente novamente.|
|Determinadas configurações do banco de dados de navegação do IntelliSense estão desabilitadas.|Determinadas configurações do IntelliSense podem ser desabilitadas no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **opções** caixa de diálogo.|Ative as configurações para habilitá-las.<br /><br /> Consulte [opções, Editor de texto, C/C++, avançado](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|A mensagem **métodos desconhecido** aparece em um nó de método.<br /><br /> Esse problema ocorre porque o nome do método não pode ser resolvido.|O arquivo binário não pode ter uma tabela de realocação de base.|Ativar o **/fixed:** opção de vinculador.|
||Talvez o arquivo de banco de dados do programa (.pdb) não tenha sido compilado.<br /><br /> Um arquivo .pdb armazena informações de depuração, como o tipo, o método e as informações do arquivo de origem.|Ativar o **/Debug** opção de vinculador.|
||Não é possível abrir ou encontrar o arquivo .pdb em locais esperados.|Verifique se o arquivo .pdb existe nos locais esperados.|
||As informações de depuração foram removidas do arquivo .pdb.|Se o **/PDBSTRIPPED** opção foi usada no vinculador, inclua o arquivo. PDB completo em vez disso.|
||O chamador não é uma função, e é uma conversão no arquivo binário ou um ponteiro na seção de dados.|Quando o chamador for uma conversão, tente usar `_declspec(dllimport)` para evitá-la.|

##  <a name="RenderMoreQuickly"></a> Tornar o código mapas processam mais rapidamente
 Quando você gera um mapa pela primeira vez, o Visual Studio índices todas as dependências que encontrar. Esse processo pode levar algum tempo, especialmente para grandes soluções, mas melhorará o desempenho mais tarde. Se o código for alterado, o Visual Studio índices novamente apenas o código atualizado. Para minimizar o tempo necessário concluir a renderização do mapa, considere o seguinte:

-   [Mapear apenas as dependências que lhe interessam.](#SeeSpecificSource)

-   Antes de gerar o mapa de uma solução inteira, reduza o escopo da solução.

-   Desativar a criação automática para a solução com o **Skip Build** na barra de ferramentas de mapa de código.

-   Desativar a adição automática de itens pai com a **incluem pais** na barra de ferramentas de mapa de código.

-   Edite o arquivo de mapa de código diretamente para remover nós e links que não é necessário. Alterar o mapa não afeta o código subjacente. Consulte [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

 ![Botões SKIP Build e incluir pais](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")

 Embora o Visual Studio pode executar com 1 GB de memória, é recomendável que o computador tem pelo menos 2 GB de memória para evitar atrasos longos, enquanto o Visual Studio cria o índice de código e gera o mapa.

 Pode levar mais tempo para criar mapas ou adicionar itens a um mapa do Gerenciador de soluções quando um item de projeto **copiar para diretório de saída** está definida como **copiar sempre**. Isso pode causar problemas em compilações incrementais e fazer o Visual Studio recompilar o projeto sempre. Para aumentar o desempenho, altere essa propriedade como **copiar se mais recente** ou `PreserveNewest`. Consulte [compilações incrementais](../msbuild/incremental-builds.md).

 O mapa concluído mostrará dependências somente para código compilado com êxito. Se ocorrerem erros de compilação para determinados componentes, esses erros aparecem no mapa. Certifique-se de que um componente, na verdade, compilações e tem dependências antes de tomar decisões de arquitetura baseadas no mapa.

##  <a name="SavingExporting"></a> Mapas de códigos de compartilhamento

### <a name="share-the-map-with-other-visual-studio-users"></a>Compartilhar o mapa com outros usuários do Visual Studio

Use o **arquivo** menu para salvar o mapa.

-ou-

Para salvar o mapa como parte do projeto específico, na barra de ferramentas do mapa, escolha **compartilhamento**, **mover** \< *CodeMapName*>**.dgml em**e, em seguida, escolha o projeto em que você deseja salvar o mapa.

![Mover um mapa em outro projeto](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")

O Visual Studio salva o mapa como um arquivo de .dgml que você pode compartilhar com outros usuários do Visual Studio Enterprise e no Visual Studio Professional.

> [!NOTE]
>  Antes de compartilhar um mapa com aqueles que usam o Visual Studio Professional, certifique-se expandir todos os grupos, Mostrar nós ocultos e links entre grupos e recuperar todos os nós excluídos que você deseja ver em seu mapa. Do contrário, outros usuários não poderão consultar esses itens.
>
>  O seguinte erro pode ocorrer quando você salvar um mapa que está em um projeto de modelagem ou foi copiado de um projeto de modelagem para outro local:
>
>  "Não é possível salvar *fileName* fora do diretório do projeto. Itens vinculados não são compatíveis."
>
>  O Visual Studio mostra o erro, mas cria a versão salva de qualquer maneira. Para evitar o erro, crie o mapa fora do projeto de modelagem. Em seguida, é possível salvá-lo no local desejado. Apenas copiar o arquivo para outro local na solução e, em seguida, tentar salvá-lo não funcionará.

### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Exportar o mapa como uma imagem para que você possa copiá-lo em outros aplicativos, como Microsoft Word ou PowerPoint

1.  Na barra de ferramentas do mapa de código, escolha **compartilhamento**, **Email como imagem** ou **Copiar imagem**.

2.  Cole a imagem em outro aplicativo.

### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Exportar o mapa como um arquivo XPS, para que você pode vê-lo nos visualizadores XML ou XAML, como o Internet Explorer

1.  Na barra de ferramentas do mapa de código, escolha **compartilhamento**, **Email como portátil XPS** ou **Salvar como XPS portátil**.

2.  Navegue para onde você deseja salvar o arquivo.

3.  Nome do mapa de código. Verifique se o **Salvar como tipo** caixa é definida para **arquivos XPS (\*. XPS)**. Escolha **salvar**.

## <a name="what-else-can-i-do"></a>O que mais posso fazer?

-   [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Mapear métodos na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

-   [Encontrar possíveis problemas usando analisadores de mapa de códigos](../modeling/find-potential-problems-using-code-map-analyzers.md)

-   [Procurar e reorganizar mapas de códigos](../modeling/browse-and-rearrange-code-maps.md)

-   [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
