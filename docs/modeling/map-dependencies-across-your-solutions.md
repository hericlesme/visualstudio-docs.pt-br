---
title: Mapas de código
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 553e2437abc2d8f498b556300a9266c9e79297f7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265559"
---
# <a name="map-dependencies-with-code-maps"></a>Mapear as dependências com mapas de código

Você pode visualizar as dependências em seu código, criando um mapa de código. Código mapeia ajudam que você a ver como o código se encaixa sem ler arquivos e linhas de código.

![Exibir dependências nas soluções](../modeling/media/codemapsmainintro.png)

Para usar mapas de código, você precisa do Visual Studio Enterprise ou Professional edition. A funcionalidade de mapa de código no Professional edition é um pouco mais limitada que no Enterprise edition.

> [!NOTE]
> Antes de compartilhar mapas criados no Visual Studio Enterprise com outras pessoas que usam o Visual Studio Professional, certifique-se de que todos os itens do mapa (como itens ocultos, grupos expandidos e links entre grupos) são visíveis.

Você pode mapear as dependências para código nestes idiomas:

- Visual c# ou Visual Basic em uma solução ou assemblies (*. dll* ou *.exe*)

- Código C ou C++ nativo ou gerenciado em projetos do Visual C++, arquivos de cabeçalho (*. h* ou `#include`), ou binários

- Projetos e assemblies do X++ feitos com base nos módulos do .NET para Microsoft AX Dynamics

> [!NOTE]
> Para projetos que não seja o c# ou Visual Basic, há menos opções para iniciar um mapa de código ou adicionar itens a um mapa de código existente. Por exemplo, você não pode clique um objeto no editor de texto de um projeto de C++ e adicioná-lo a um mapa de código. No entanto, você pode arrastar e soltar elementos de código individuais ou os arquivos de **Solution Explorer**, **exibição de classe**, e **Pesquisador de objetos**.

## <a name="install-code-map-and-live-dependency-validation"></a>Mapa de código de instalação e validação de dependência dinâmica

Para criar um mapa de código no Visual Studio de 2017, primeiro instale o **mapa de códigos** e **Live validação de dependência** componentes:

1. Abra **instalador do Visual Studio**. Você pode abri-lo no menu Iniciar do Windows ou no Visual Studio selecionando **ferramentas** > **obter ferramentas e recursos**.

1. Selecione a guia **Componentes individuais**.

1. Role para baixo até o **ferramentas código** seção e selecione **mapa de códigos** e **Live validação de dependência**.

   ![Componentes de mapa de código e validação de dependência em tempo real no instalador do Visual Studio](media/modeling-components.png)

1. Selecione **Modificar**.

   O **mapa de códigos** e **Live validação de dependência** componentes começam a instalação. Você poderá ser solicitado a fechar o Visual Studio.

## <a name="add-a-code-map"></a>Adicionar um mapa de código

Você pode criar um mapa de código vazio e arraste itens para ele, incluindo referências de assembly, arquivos e pastas, ou você pode gerar um mapa de código para todos ou parte de sua solução.

Para adicionar um mapa de código vazio:

1. Em **Solution Explorer**, abra o menu de atalho para o nó da solução de nível superior. Escolha **adicionar** > **Novo Item**.

2. No **Adicionar Novo Item** caixa de diálogo, em **instalado**, escolha o **geral** categoria.

3. Escolha o **Document(.dgml) de gráfico direcionado** modelo e selecione **adicionar**.

   > [!TIP]
   > Para este modelo não pode aparecer em ordem alfabética, role até o final da lista de modelos, se você não estiver visível.

   Um mapa em branco aparece em sua solução **itens de solução** pasta.

Da mesma forma, você pode criar um novo arquivo de mapa de código sem adicioná-lo à sua solução selecionando **arquitetura** > **novo mapa de código** ou **arquivo**  >  **Novo** > **arquivo**.

## <a name="generate-a-code-map-for-your-solution"></a>Gerar um mapa de código para sua solução

Para ver todas as dependências em sua solução:

1. Na barra de menus, escolha **arquitetura** > **gerar mapa de código para solução**. Se seu código não foi alterado desde a última vez que você o criou, você pode selecionar **arquitetura** > **gerar mapa de código para solução sem compilação** em vez disso.

   ![Gerar um comando de mapa](../modeling/media/codemapsarchitecturemenu.png)

   É gerado um mapa que mostra os assemblies de nível superior e agregados links entre eles. Quanto maior o vínculo agregado, mais dependências ele representa.

2. Use o **legenda** botão na barra de mapa de código para mostrar ou ocultar a lista de ícones de tipo de projeto (como teste, Web e projeto Phone), itens de código (como Classes, métodos e propriedades) e tipos de relação (como herda de Implementa e chamadas).

   ![Gráfico de dependência de nível superior de assemblies](../modeling/media/dependencygraph_toplevelassemblies.png)

   Esta solução de exemplo contém pastas de solução (**testes** e **componentes**), assemblies, projetos da Web e projetos de teste. Por padrão, todas as relações de confinamento aparecem como *grupos*, que você pode expandir e recolher. O **externos** grupo contiver qualquer coisa fora de sua solução, incluindo dependências de plataforma. Os assemblies externos mostram apenas os itens usados. Por padrão, os tipos de base do sistema estão ocultos no mapa para reduzir a desordem.

3. Para analisar o mapa, expanda os grupos que representam os projetos e assemblies. Você pode expandir tudo pressionando **CTRL + A** para selecionar todos os nós e, em seguida, escolhendo **grupo**, **expandir** no menu de atalho.

   ![Expandir todos os grupos em um mapa de código](../modeling/media/codemapsexpandallgroups.png)

4. No entanto, isso não pode ser útil para uma solução grande. Na verdade, soluções complexas, as limitações de memória podem impedir que você expandir todos os grupos. Em vez disso, para ver dentro de um nó individual, expandi-lo. Mova o ponteiro do mouse sobre o nó e, em seguida, clique na divisa (seta para baixo) quando ele for exibido.

   ![Expandindo um nó em um mapa de código](../modeling/media/dependencygraph_containment.png)

   Ou use o teclado selecionando o item e pressionando a tecla de mais (**+**). Para explorar níveis mais profundos do código, faça o mesmo para namespaces, tipos e membros.

   > [!TIP]
   > Para obter mais detalhes sobre como trabalhar com o código de mapas usando o mouse, teclado e toque, consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

5. Para simplificar o mapa e focar nas partes individuais, escolha **filtros** na barra de ferramentas de mapa de código e selecione apenas os tipos de nós e links que lhe interessam. Por exemplo, você pode ocultar todas as pastas de solução e Assembly recipientes.

   ![Simplificar o mapa filtrando contêineres](../modeling/media/codemapsfilterfoldersassemblies.png)

   Você também pode simplificar o mapa, ocultando ou removendo grupos individuais e itens do mapa, sem afetar o código subjacente da solução.

6. Para ver as relações entre itens, selecione-os no mapa. As cores dos links indicam os tipos de relação, como mostra o **legenda** painel.

   ![Exibir dependências nas soluções](../modeling/media/codemapsmainintro.png)

   Neste exemplo, os links roxos são chamadas, pontilhados links são referências e os links de azuis claras são acesso ao campo. Links verde pode ser herança, ou eles podem ser *agregar links* que indicam mais de um tipo de relação (ou *categoria*).

   > [!TIP]
   > Se você vir um link verde, ele pode não significar que exista apenas uma relação de herança. Também podem ser chamadas de método, mas estão ocultas pela relação de herança. Para consultar tipos específicos de links, use as caixas de seleção no **filtros** painel para ocultar os tipos não estiver interessado em.

7. Para obter mais informações sobre um item ou link, mova o ponteiro sobre ele até que uma dica de ferramenta é exibida. Mostra detalhes de um elemento de código ou as categorias que representa um link.

   ![Mostrar as categorias de uma relação](../modeling/media/codemapsshowlinkcatgories.png)

8. Para examinar os itens e dependências representadas por um link de agregação, primeiro selecione o link e, em seguida, abra o menu de atalho. Escolha **Mostrar Links participantes** (ou **Mostrar Links participantes no novo mapa de código**). Isso expande os grupos em ambas as extremidades do link e mostra somente os itens e as dependências que participam no link.

9. Para focar nas partes específicas do mapa, você pode continuar a remover itens que você não estiver interessado em. Por exemplo, para detalhar o modo de exibição de classe e de membro, simplesmente filtrar todos os nós no namespace de **filtros** painel.

   ![Busca detalhada em nível de classe e membro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Outra maneira de foco em um mapa de solução complexa é gerar um novo mapa que contém os itens selecionados em um mapa existente. Manter **Ctrl** enquanto seleciona os itens que você deseja se concentrar, abra o menu de atalho e escolha **novo gráfico da seleção**.

   ![Mostrar itens selecionados em um novo mapa de código](../modeling/media/codemapsshowonnewmap.png)

11. O contexto de recipiente é transportado para o novo mapa. Ocultar pastas de solução e quaisquer outros contêineres que você não deseja ver usando o **filtros** painel.

   ![Os contêineres para simplificar a exibição de filtro](../modeling/media/codemapsexpandnewgroups.png)

12. Expanda os grupos e selecione os itens no mapa para exibir as relações.

   ![Selecionar itens para exibir as relações](../modeling/media/codemapsviewnewrelationships.png)

Consulte também:

- [Procurar e reorganizar mapas de códigos](../modeling/browse-and-rearrange-code-maps.md)
- [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Encontrar possíveis problemas em seu código por [executando um analisador](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Exibir dependências específicas em um mapa de código

Suponha que você tenha uma revisão de código para executar em alguns arquivos com alterações pendentes. Para ver as dependências nessas alterações, você pode criar um mapa de código desses arquivos.

   ![Mostrar dependências específicas em um mapa de código](../modeling/media/codemapsspecificdependenciesintro.png)

1. Em **Solution Explorer**, selecione os projetos, referências de assembly, pastas, arquivos, tipos ou membros que você deseja mapear.

   ![Selecione os itens que você deseja mapear](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Sobre o **Gerenciador de soluções** barra de ferramentas, escolha **Mostrar no mapa de códigos** ![criar novo gráfico selecionado nós botão de](../modeling/media/createnewgraphfromselectedbutton.gif). Ou então, abra o menu de atalho para um ou um grupo de itens e escolha **Mostrar no mapa de códigos**.

   Você também pode arrastar itens das **Solution Explorer**, **exibição de classe**, ou **Pesquisador de objetos**, em um [novo](#add-a-code-map) ou código existente do mapa. Para incluir a hierarquia pai para os itens, pressione e segure o **Ctrl** pressionada enquanto você arrasta os itens ou usar o **incluem pais** botão na barra de mapa de código para especificar a ação padrão. Você também pode arrastar os arquivos de assembly de fora do Visual Studio, como de **Windows Explorer**.

   > [!NOTE]
   > Quando você adiciona itens de um projeto que é compartilhado entre vários aplicativos, como o Windows Phone ou da Microsoft Store, esses itens aparecem no mapa com o projeto de aplicativo ativa no momento. Se você alterar o contexto para outro projeto de aplicativo e adicionar mais itens do projeto compartilhado, esses itens agora serão exibidos com o projeto de aplicativo recém-ativo. Operações realizadas com um item no mapa se aplicam apenas aos itens que compartilham o mesmo contexto.

3. O mapa mostra os itens selecionados dentro de seus assemblies que contêm.

   ![Itens selecionados mostrados como grupos no mapa](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Para explorar itens, expanda-os. Mova o ponteiro do mouse sobre um item e clique no ícone de divisa (seta para baixo) quando ele for exibido.

   ![Expanda um nó em um mapa de código](../modeling/media/dependencygraph_containment.png)

   Para expandir todos os itens, selecione-os usando **Ctrl**+**um**, em seguida, abra o menu de atalho para o mapa e escolha **grupo**  >   **Expanda**. No entanto, essa opção não estará disponível se expandir todos os grupos cria um mapa inutilizável ou problemas de memória.

5. Continue a expandir itens que você está interessado, chegando até o nível de classe e de membro, se necessário.

   ![Expanda grupos de nível de classe e membro](../modeling/media/codemapsexpandtoclassandmember.png)

   Para ver os membros no código, mas não são exibidos no mapa, clique o **filhos buscar novamente** ícone ![buscar novamente filhos ícone](../modeling/media/dependencygraph_deletednodesicon.png) no canto superior esquerdo de um grupo.

6. Para ver mais itens relacionados no mapa, selecione um e escolha **Mostrar relacionados** na barra de ferramentas de mapa de código, selecione o tipo de itens relacionados para adicionar ao mapa. Como alternativa, selecione um ou mais itens, abra o menu de atalho e escolha o **Mostrar** opção para o tipo de itens relacionados para adicionar ao mapa. Por exemplo:

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

    ![Mostrar métodos chamados por este membro](../modeling/media/codemapsshowrelatedmethods.png)

7. O mapa mostra as relações. Neste exemplo, o mapa mostra os métodos chamados pelo `Find` método e sua localização na solução ou externamente.

   ![Mostrar dependências específicas em um mapa de código](../modeling/media/codemapsspecificdependenciesintro.png)

8. Para simplificar o mapa e focar nas partes individuais, escolha **filtros** na barra de ferramentas de mapa de código e selecione apenas os tipos de nós e links que lhe interessam. Por exemplo, desative a exibição de pastas de solução, Assemblies e Namespaces.

   ![Use o painel de filtro para simplificar a exibição](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Consulte também

- [Vídeo: entender o design de código com mapas de código do Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)]
- [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapear métodos na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Encontrar possíveis problemas usando analisadores de mapa de códigos](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procurar e reorganizar mapas de códigos](../modeling/browse-and-rearrange-code-maps.md)
- [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
