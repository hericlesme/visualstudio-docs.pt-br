---
title: "Procurar e reorganizar mapas de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2ac958d6033408ab509cfca7372dec0f7360b48c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="browse-and-rearrange-code-maps"></a>Procurar e reorganizar mapa de códigos
Reorganize itens em mapas de código para torná-los mais fáceis de ler e melhorar o desempenho.  
  
 Você pode personalizar mapas de código sem afetar o código subjacente em uma solução. Isso é útil quando você deseja se concentrar em elementos de código de tecla ou comunicar ideias sobre o código. Por exemplo, para realçar áreas interessantes, você pode selecionar elementos no mapa de código e filtrá-los, alterar o estilo dos elementos de código e links, ocultar ou excluir elementos de código e organizar os elementos de código usando propriedades, categorias ou grupos.  
  
 **Requisitos**  
  
-   Para criar mapas de código, você deve ter o Visual Studio Enterprise.  
  
-   Você pode exibir mapas de código e fazer edições limitadas em mapas de código no Visual Studio Professional.  
  
##  <a name="ManageLargeGraphs"></a>Começar a trabalhar com mapas de código  
 Criar um mapa de código (consulte [mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md) para obter mais detalhes). Se você não quiser aguardar o mapa concluir a geração, clique o **Cancelar** link a qualquer momento para parar o processo de geração. No entanto, você não verá os detalhes de todas as dependências e links se você fizer isso.  
  
 Depois de gerar o mapa, começar com estas dicas para revisar seu código:  
  
-   Examinar os clusters de dependência natural no código. Na barra de ferramentas do mapa, escolha **Layout**, **Clusters rápidos**![botão Clusters rápidos na barra de ferramentas de gráfico](../modeling/media/quickclustersicon.gif "QuickClustersIcon"). Consulte [alterar o layout de mapa](#Selecting).  
  
     ![Gráfico de dependência &#45; Layout de Clusters rápido](../modeling/media/dependencygraph_quickclusters.png "DependencyGraph_QuickClusters")  
  
-   Organize o mapa em áreas pequenas, agrupando nós relacionados. Recolhe os grupos para ver apenas as dependências intergroup, que aparecem automaticamente. Consulte [nós de grupo](#OrganizeGroups).  
  
-   Use filtros para simplificar o mapa e concentre-se nos tipos de nós ou links que lhe interessam. Consulte [filtrar nós e links](#FilterNodes).  
  
-   Maximize o desempenho de mapas grandes. Consulte [mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md) para obter mais informações. Por exemplo, ativar **Skip Build** na barra de ferramentas mapa para que o Visual Studio não recriar sua solução quando você atualiza os itens do mapa.  
  
##  <a name="Selecting"></a>Alterar o layout de mapa  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Organize o fluxo de dependência para o mapa inteiro em uma direção específica. Isso pode ajudá-lo a camadas arquitetônicas no código.|Na barra de ferramentas do mapa, escolha **Layout**e, em seguida:<br /><br /> -   **Cima para baixo** ![superior do botão de gráfico inferior](../modeling/media/topbottomgraphbutton.gif "TopBottomGraphButton")<br />-   **Baixo para cima** ![inferior ao botão gráfico superior](../modeling/media/bottomtopgraphbutton.gif "BottomTopGraphButton")<br />-   **Da esquerda para a direita** ![da esquerda para o botão direito do layout](../modeling/media/leftrightgraphbutton.gif "LeftRightGraphButton")<br />-   **Direita para a esquerda** ![direita para o botão esquerdo do gráfico](../modeling/media/rightleftgraphbutton.gif "RightLeftGraphButton")|  
|Consulte clusters natural de dependência no código com os nós mais dependentes no Centro de clusters e os nós menos dependentes fora desses clusters.|Na barra de ferramentas do mapa, escolha **Layout**e, em seguida, **Clusters rápidos**![botão Clusters rápidos na barra de ferramentas de gráfico](../modeling/media/quickclustersicon.gif "QuickClustersIcon").|  
|Selecione um ou mais nós do mapa.|Clique em um nó para selecioná-la. Para marcar ou desmarcar a mais de um nó, mantenha **CTRL** enquanto clica.<br /><br /> Teclado: pressione **guia** ou use as teclas de direção para mover o retângulo de foco pontilhada para um nó e pressione **espaço** para selecioná-la. Pressione **CTRL** + **espaço** para seleção múltipla ou cancele a seleção de nós.|  
|Mova os nós específicos no mapa.|Arraste nós para movê-las. Para mover os outros nós e links de forma que você arrasta nós, pressione e segure o **SHIFT** chave.<br /><br /> Teclado: manter **CTRL** e pressione as teclas de direção.|  
|Altere o layout dentro de um grupo, independentemente de outros nós e grupos no mapa.|Selecione um nó e abra o menu de atalho. Escolha **Layout** e selecione um estilo de layout.<br /><br /> - ou -<br /><br /> Selecione um nó e expandi-lo e mostra os nós filhos. Clique no título de nó para mostrar a barra de ferramentas pop-up do grupo e abrir o **alterar o estilo de layout do grupo de**![gráfico de dependência &#45; barra de ferramentas do grupo &#45; layout](../modeling/media/dependencygraph_grouptoolbar.gif "DependencyGraph_ GroupToolbar") lista. Selecione um dos layouts de árvore, **Clusters rápidos**, ou **exibição de lista** (que organiza o conteúdo de grupo em uma lista).<br /><br /> Consulte [nós de grupo](#OrganizeGroups) para obter mais detalhes.|  
|Desfazer uma ação no mapa.|Pressione **CTRL** + **Z** ou use o Visual Studio **desfazer** comando.|  
  
##  <a name="Explore"></a>Procurar o mapa  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Verificar o mapa.|Arraste o mapa em qualquer direção usando o mouse.<br /><br /> - ou -<br /><br /> Manter **SHIFT** e gire a roda do mouse para rolar horizontalmente. Manter **SHIFT** + **CTRL** e gire a roda do mouse para rolar horizontalmente.|  
|Amplie ou reduzir o mapa.|Gire a roda do mouse.<br /><br /> - ou -<br /><br /> Use o **Zoom** lista suspensa na barra de ferramentas de mapa de código.<br /><br /> - ou -<br /><br /> Use os atalhos de teclado. Para aumentar o zoom, pressione **CTRL + SHIFT +.** (ponto). Para reduzir, pressione **CTRL + SHIFT +,** (vírgula).|  
|Amplie uma área específica usando o mouse.|Mantenha o botão direito do mouse ao desenhar um retângulo ao redor da área que lhe interessam.|  
|Redimensionar e ajustar o mapa em sua janela.|Escolha **Ajustar nível de Zoom** do **Zoom** lista na barra de ferramentas de mapa de código.<br /><br /> - ou -<br /><br /> Clique o **Aplicar Zoom para ajustar** ícone ![ícone Zoom na barra de ferramentas do mapa](../modeling/media/almcodemapzoomicon.png "ALMCodeMapZoomIcon") na barra de ferramentas de mapa de código. Teclado: pressione **CTRL + 0** (zero).|  
|Localize um nó no mapa por seu nome. **Dica:** isso funciona somente para itens no mapa. Para localizar itens em sua solução, mas não no mapa, encontrá-los no **Solution Explorer**e, em seguida, arraste-os para o mapa. (Arraste sua seleção ou na barra de ferramentas do Gerenciador de soluções, clique em **Mostrar no mapa de códigos**).|1.  Escolha o **localizar** ícone ![ícone localizar na barra de ferramentas do mapa](../modeling/media/almcodemapfindicon.png "ALMCodeMapFindIcon") na barra de ferramentas de mapa de código (teclado: pressione **CTRL + F**) para mostrar a caixa de pesquisa no canto superior direito do mapa.<br />2.  Digite o nome do item e pressione **retornar** ou clique no ícone "Lupa". O primeiro item que corresponde a sua pesquisa aparece selecionado no mapa.<br />3.  Para personalizar sua pesquisa, abra a lista suspensa e escolha uma opção de pesquisa. As opções são **Localizar próximo**, **Localizar anterior**, e **Selecionar tudo**. Em seguida, clique no botão correspondente ao lado da caixa de texto de pesquisa.<br />     ![Pesquisar a lista de opções &#45; para baixo a lista](../modeling/media/almcodemapssearchdropdown.png "ALMCodeMapsSearchDropDown")<br />     Como alternativa, use o teclado: pressione **F3** para selecionar o próximo nó correspondente ou **SHIFT + F3** para selecionar o nó correspondente anterior.<br />4.  Selecione qualquer uma das opções que especificam como os termos de pesquisa são tratados clicando nos ícones abaixo a caixa de texto de pesquisa.<br />     ![Opções de correspondência de pesquisa](../modeling/media/almcodemapssearchmatchicons.png "ALMCodeMapsSearchMatchIcons")<br />     As opções são, da esquerda para a direita, caso correspondência confidenciais, somente palavras inteiras, usar sintaxe de expressão regular do .NET, expandir automaticamente os grupos para mostrar as correspondências entre itens. **Importante:** você pode usar a caixa de pesquisa para localizar correspondências em grupos recolhidos somente se os grupos foram previamente expandidos. Para localizar esses correspondências e expandir seus grupos pai automaticamente, escolha esta opção na caixa de pesquisa.|  
|Selecione todos os nós não selecionados.|Abra o menu de atalho para os nós selecionados. Escolha **selecione**, **Inverter seleção**.|  
|Selecione nós adicionais que vinculam às selecionado.|Abra o menu de atalho para os nós selecionados. Escolha **selecione** e uma destas opções:<br /><br /> -Para selecionar nós adicionais que vinculam diretamente para o nó selecionado, escolha **dependências de entrada**.<br />-Para selecionar nós adicionais que vinculam diretamente do nó selecionado, escolha **dependências de saída**.<br />-Para selecionar nós adicionais que o link de e para o nó selecionado, escolha **ambos**.<br />-Para selecionar todos os nós que o link de e para o nó selecionado, escolha **subgráfico conectado**.<br />-Para selecionar todos os filhos do nó selecionado, escolha **filhos**.|  
  
##  <a name="FilterNodes"></a>Nós de filtro e links  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Mostrar ou ocultar o painel de filtros.|Escolha o **filtros** na barra de ferramentas de mapa de código. Por padrão, o painel de filtros é exibido como uma página com guias na janela do Gerenciador de soluções.|  
|Filtre os tipos de nós que são mostrados no mapa.|Marque ou desmarque as caixas de seleção no **elementos de código** lista no painel de filtros.|  
|Filtre os tipos de links são mostrados no mapa.|Marque ou desmarque as caixas de seleção no **relações** lista no painel de filtros.|  
|Mostrar ou ocultar nós de projeto de teste no mapa.|Definir ou limpar o **ativos de teste** caixa de seleção de **diversos** lista no painel de filtros.|  
  
 Os ícones mostrados no painel de legenda do mapa refletem as configurações que você faz na lista. Para mostrar ou ocultar o painel de legenda, clique o **legenda** na barra de ferramentas de mapa de código.  
  
##  <a name="Inspect"></a>Examine nós e links  
 Mapas de código mostram esses tipos de links:  
  
-   Um link individual representa uma única relação entre dois nós.  
  
-   Um link entre grupos representa uma relação entre dois nós em diferentes grupos.  
  
-   Um link agregado representa todas as relações que aponte na mesma direção entre dois grupos.  
  
> [!TIP]
>  Por padrão, o mapa mostra links entre grupos somente para nós selecionados. Para alterar esse comportamento para mostrar ou ocultar agregados links entre grupos, clique em **Layout** no código de mapear a barra de ferramentas e escolha **avançado**, em seguida, **Mostrar todos os Links entre grupos** ou **Ocultar todos os Links entre grupos**. Consulte [ocultar ou Mostrar nós e links](#HidingShowing) para obter mais detalhes.  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Consulte para obter mais informações sobre um nó ou um link.|Mova o ponteiro do mouse sobre o nó ou link até que uma dica de ferramenta é exibida.<br /><br /> A dica de ferramenta para um link agregado lista as dependências individuais que ele representa.<br /><br /> - ou -<br /><br /> Abra o menu de atalho para o nó ou link. Escolha **editar**, **propriedades**.|  
|Mostrar ou ocultar o conteúdo de um grupo.|-Para expandir um grupo, abra o menu de atalho para o nó e escolha **grupo**, **expandir**.<br />     - ou -<br />     Mova o ponteiro do mouse sobre o nó até que o botão de divisa (seta para baixo) é exibido. Clique neste botão para expandir o grupo. Teclado: para expandir ou recolher o grupo selecionado, pressione a **mais** chave (**+**) ou o **menos** chave ( **-** ).<br />-Para recolher um grupo, abra o menu de atalho para o nó e escolha **grupo**, **recolher**.<br />     - ou -<br />     Mova o ponteiro do mouse sobre um grupo até que seja exibido no botão de divisa (seta para cima). Clique neste botão para recolher o grupo.<br />-Para expandir todos os grupos, pressione **CTRL** + **um** para selecionar todos os nós. Abra o menu de atalho para o mapa e escolha **grupo**, **expandir**. **Observação:** este comando não estará disponível se expandir todos os grupos de gerar problemas de memória ou um mapa inutilizável. É recomendável que você expandir o mapa somente para o nível de detalhes importantes para você.<br />-Para recolher todos os grupos, abra o menu de atalho de um nó ou para o mapa. Escolha **grupo**, **Recolher tudo**.|  
|Consulte a definição de código de um namespace, tipo ou membro.|Abra o menu de atalho para o nó e escolha **ir para definição**.<br /><br /> -ou-<br /><br /> Clique duas vezes no nó. Para grupos expandidos, clique duas vezes o cabeçalho de grupo.<br /><br /> -ou-<br /><br /> Selecione o nó e pressione **F12**.<br /><br /> Por exemplo:<br /><br /> -Para um namespace que contém uma classe, o arquivo de código para a classe abre para mostrar a definição de classe. Em outros casos, o **localizar resultados de símbolos** janela mostra uma lista de arquivos de código. **Observação:** quando você executar essa tarefa em um namespace do Visual Basic .NET, o arquivo de código por trás de namespace não abre. Esse problema também ocorre quando você executar essa tarefa em um grupo de nós selecionados que incluem um namespace do Visual Basic .NET. Para contornar esse problema, navegar manualmente para o arquivo de código por trás de namespace ou omita o nó para o namespace de sua seleção.<br />-Para uma classe ou uma classe parcial, o arquivo de código para essa classe é aberto para exibir a definição de classe.<br />-Para um método, o arquivo de código para a classe pai abre para mostrar a definição de método.|  
|Examine as dependências e itens que participam de um link de agregação.|Selecione os links que você está interessado e abra o menu de atalho de sua seleção. Escolha **Mostrar Links participantes** ou **Mostrar Links participantes no novo mapa de código**.<br /><br /> O Visual Studio expande os grupos em ambas as extremidades do link e mostra apenas esses itens e dependências que participam do link. **Observação:** ao examinar as dependências entre os itens em grupos parciais, você poderá ver esse comportamento: <ul><li>Links para itens que não participam analisá desaparecem do mapa, embora esses links ainda existem.</li><li>Suponha que você examina um link para um item em um grupo parcial e examina um link diferentes no mesmo item mais tarde. Durante o exame de segundo, o grupo de destino parcial mostra apenas os itens de seu primeiro exame. Não são exibidos links e itens de destino que não participam de seu primeiro exame mas participem de seu segundo exame.</li></ul> Para ver itens de um grupo ausentes, escolha **filhos buscar novamente**![buscar novamente filhos ícone](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") (que indica que nem todos os membros de um grupo de aparecer no mapa). Você também pode tentar suas ações de desfazer (teclado: pressione **CTRL + Z**) e examine as dependências em um mapa de novo.|  
|Examine as dependências em vários nós em diferentes grupos.|Expanda os grupos para que você possa ver todos os seus filhos. Selecione todos os nós que lhe interessam, incluindo seus filhos. O mapa mostra os links entre grupos entre os nós selecionados.<br /><br /> Para selecionar todos os nós em um grupo, pressione e segure **SHIFT** e o botão esquerdo do mouse enquanto você desenhar um retângulo ao redor do grupo. Para selecionar todos os nós em um mapa, pressione **CTRL**+**um**. **Dica:** para mostrar os links entre grupos em todos os momentos, escolha **Layout** na barra de ferramentas mapa **avançado**, **Mostrar todos os Links entre grupos**.|  
|Consulte os itens que faz referência a um nó ou link.|Abra o menu de atalho para o nó e escolha **localizar todas as referências**. **Observação:** isso se aplica somente quando o `Reference` atributo está definido para o nó ou link no arquivo de .dgml do mapa. Para adicionar referências a itens de nós ou links, consulte [mapeia Personalizar código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|  
  
##  <a name="HidingShowing"></a>Ocultar ou Mostrar nós e links  
 Ocultar nós os impede de participar de algoritmos de layout. Por padrão, links de grupo cruzado permanecem ocultos. Links de grupo cruzado são links individuais que conectam nós entre os grupos. Quando os grupos são recolhidos, o mapa agrega todos os links entre grupos em único links entre grupos. Quando você expande um grupo e seleciona nós dentro do grupo, os links de grupo cruzado são exibidos e mostram as dependências nesse grupo.  
  
> [!CAUTION]
>  Antes de compartilhar um mapa que foi criado no Visual Studio Enterprise com aqueles que usam o Visual Studio Professional, certifique-se reexibir quaisquer nós ou links entre grupos que você deseja que outras pessoas vejam. Do contrário, os usuários não poderão reexibir esses itens.  
  
### <a name="to-hide-or-show-nodes"></a>Para ocultar ou mostrar nós  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Oculte nós selecionados.|1.  Selecione os nós que você deseja ocultar.<br />2.  Abra o menu de atalho para os nós selecionados ou para o mapa. Escolha **selecione**, **ocultar selecionado**.|  
|Oculte nós não selecionados.|1.  Selecione nós que você deseja manter visíveis.<br />2.  Abra o menu de atalho para os nós selecionados ou para o mapa. Escolha **selecione**, **ocultar desmarcado**.|  
|Mostra nós ocultos.|-Para mostrar todos os nós ocultos dentro de um grupo, primeiro verifique se que o grupo é expandido. Abra o menu de atalho e escolha **selecione**, **reexibir filhos**.<br />     - ou -<br />     Clique o **reexibir filhos**![reexibir filhos ícone](../modeling/media/dependencygraph_filtericon_hiddennodes.gif "DependencyGraph_FilterIcon_HiddenNodes") ícone no canto superior esquerdo do grupo (Isso é visível apenas quando Há nós ocultos filho).<br />-Para mostrar todos os nós ocultos, abra o menu de atalho para o mapa ou um nó e escolha **selecione**, **reexibir todas as**.|  
  
### <a name="to-hide-or-show-links"></a>Para ocultar ou Mostrar links  
  
|**To**|**Na barra de ferramentas do mapa, escolha o Layout, Avançado e, em seguida, escolha**|  
|------------|----------------------------------------------------------------------|  
|Mostra links entre grupos em todos os momentos.|**Mostrar todos os Links entre grupos**. Isso oculta links agregados entre grupos.|  
|Oculte links entre grupos em todos os momentos.|**Ocultar todos os Links entre grupos**|  
|Mostre apenas os links entre grupos para nós selecionados.|**Mostrar Links entre grupos em nós selecionados**|  
|Oculte todos os links.|**Ocultar todos os Links**. Para exibir links novamente, escolha uma das opções listadas acima.|  
  
##  <a name="OrganizeGroups"></a>Nós de grupo  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Mostra nós de contêiner como nós de grupo ou nós folha.|Para mostrar nós de contêiner como nós folha: selecione os nós, abra o menu de atalho de sua seleção e escolha **grupo**, **converter para folha**.<br /><br /> Para mostrar nós de contêiner como nós de grupo: selecione os nós, abra o menu de atalho de sua seleção e escolha **grupo**, **converter para o grupo**.|  
|Altere o layout dentro de um grupo.|Selecione o grupo, abra o menu de atalho, escolha **Layout**e selecione o estilo de layout desejado.<br /><br /> - ou -<br /><br /> 1.  Selecione o grupo e verifique se que ele é expandido.<br />2.  Clique no cabeçalho de grupo novamente e a barra de ferramentas do grupo é exibida.<br />     ![Gráfico de dependência &#45; barra de ferramentas do grupo](../modeling/media/dependencygraph_group.png "DependencyGraph_Group")<br />3.  Abra o **alterar o estilo de layout do grupo de** lista ![gráfico de dependência &#45; barra de ferramentas do grupo &#45; layout](../modeling/media/dependencygraph_grouptoolbar.gif "DependencyGraph_GroupToolbar") e escolha o layout estilo desejado.<br /><br /> **Exibição de lista** reorganiza os membros do grupo na lista. **Gráfico de padrão** redefine o layout de grupo para o layout padrão de mapa. Para outras opções, consulte [alterar o layout de mapa](#Selecting).|  
|Adicione um nó a um grupo.|Arraste o nó para o grupo.<br /><br /> Enquanto você arrasta o nó, o Visual Studio exibe um indicador para mostrar que você está movendo o nó.<br /><br /> Também é possível arrastar nós para fora de um grupo.|  
|Adicione um nó a um nó de grupo.|Arraste o nó para o nó de destino. Você pode converter qualquer nó de destino em um grupo, adicionando nós a ele.|  
|Grupo de nós selecionados.|1.  Selecione os nós que você deseja agrupar. Uma barra de ferramentas pop-up aparece acima o último nó em que você selecionar.<br />     ![Barra de ferramentas de gráfico de dependência](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")<br />2.  Na barra de ferramentas, escolha o ícone quarto **agrupar os nós selecionados** (se o nó é expandido ele terá cinco em vez de quatro ícones). Digite o nome para o novo grupo e pressione **retornar**.<br />     - ou -<br />     Selecione os nós que você deseja agrupar e abra o menu de atalho para a sua seleção. Escolha **grupo**, **adicionar grupo de pai**, digite o nome para o novo grupo e pressione **retornar**.<br /><br /> Você pode renomear um grupo. Abra o menu de atalho para o grupo e escolha **editar**, **propriedades** para abrir a janela de propriedades do Visual Studio. No **rótulo** propriedade, renomeie o grupo conforme necessário.|  
|Remova grupos.|Selecione o grupo ou os grupos que você deseja remover. Abra o menu de atalho de sua seleção e escolha **grupo**, **remover grupo**.|  
|Remova nós de seu grupo pai.|Selecione os nós que você deseja mover. Abra o menu de atalho de sua seleção e escolha **grupo**, **remover do pai**. Isso remove nós de backup para seu avô, ou para fora do grupo se eles tiverem nenhum grupo avô.<br /><br /> - ou -<br /><br /> Selecione os nós e arraste-os para fora do grupo.|  
  
##  <a name="AddRemoveNodesLinks"></a>Adicionar, remover ou renomear nós, links e comentários  
 Você pode exibir mais ou menos itens em um mapa para fazer drill down ou para simplificar o mapa. Você também pode renomear itens e adicionar comentários aos itens.  
  
> [!CAUTION]
>  Antes de compartilhar um mapa que foi criado usando o Visual Studio Enterprise com aqueles que usam Visual Professional, certifique-se de quaisquer elementos de código que você deseja que outras pessoas vejam são visíveis no mapa. Caso contrário, os usuários não poderão recuperar os elementos de código excluído.  
  
### <a name="add-a-node-for-a-code-element"></a>Adicionar um nó para um elemento de código  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Adicione um novo nó genérico na posição atual do ponteiro do mouse.|1.  Mova o ponteiro do mouse até o local no mapa de onde você deseja colocar o novo elemento de código e pressione **inserir**.<br />     - ou -<br />     Abra o menu de atalho para o mapa e escolha **editar**, **adicionar**, **nó genérico**.<br />2.  Digite o nome para o novo nó e pressione **retornar**.|  
|Adicione um tipo específico de nó de elemento de código no local atual do ponteiro do mouse.|1.  Mova o ponteiro do mouse até o local no mapa de onde você deseja colocar o novo elemento de código e abra o menu de atalho para o mapa.<br />2.  Escolha **editar**, **adicionar**e selecione o tipo de nó que você deseja.<br />3.  Digite o nome para o novo nó e pressione **retornar**.|  
|Adicione um genérico ou um tipo de nó de elemento de código específico a um grupo.|1.  Selecione o nó de grupo e abra o menu de atalho.<br />2.  Escolha **editar**, **adicionar**e selecione o tipo de nó que você deseja.<br />3.  Digite o nome para o novo nó e pressione **retornar**.|  
|Adicionar um novo nó do mesmo tipo e vinculados, um nó existente.|1.  Selecione o elemento de código. Uma barra de ferramentas pop-up aparece acima dele.<br />     ![Barra de ferramentas de gráfico de dependência](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")<br />2.  Na barra de ferramentas, escolha o ícone de segundo **criar um nó com a mesma categoria deste nó e adicionar um novo link para ele**.<br />3.  Escolha um local no mapa para colocar o novo elemento de código e clique no botão esquerdo do mouse.<br />4.  Digite o nome para o novo nó e pressione **retornar**.|  
|Adicione um novo nó genérico que é vinculado de um elemento de código existente que tem o foco.|1.  Usando o teclado, pressione **guia** até que o elemento de código para link do tem o foco (retângulo pontilhado).<br />2.  Pressione **Alt**+**inserir**.<br />3.  Digite o nome para o novo nó e pressione **retornar**.|  
|Adicione um novo nó genérico que é vinculado a um elemento de código existente que tem o foco.|1.  Usando o teclado, pressione **guia** até que o elemento de código para vincular a tem o foco (retângulo pontilhado).<br />2.  Pressione **Alt**+**Shift**+**inserir**.<br />3.  Digite o nome para o novo nó e pressione **retornar**.|  
  
|**Para adicionar elementos de código para**|**Execute estas etapas**|  
|----------------------------------|-----------------------------|  
|Elementos de código na solução.|1.  Localizar o elemento de código em **Gerenciador de soluções**. Use o **Solution Explorer** caixa de pesquisa ou procurar a solução. **Dica:** para localizar os elementos de código que têm dependências em um tipo ou membro, abra o menu de atalho para o tipo ou membro na **Gerenciador de soluções**. Escolha a relação que lhe interessa. **Gerenciador de soluções** mostra apenas os elementos de código com as dependências especificados.<br />2.  Arraste os elementos de código que lhe interessam para a superfície do mapa. Você também pode arrastar os elementos de código de exibição de classe ou o Pesquisador de objetos.<br />     - ou -<br />     Em **Solution Explorer**, selecione os elementos de código que você deseja mapear. Em seguida, no **Solution Explorer** barra de ferramentas, clique em **Mostrar no mapa de códigos**.<br /><br /> Por padrão, a hierarquia de contêiner pai para os novos elementos de código é mostrada no mapa. Use o **incluem pais** botão na barra de mapa de código para alterar esse comportamento. Quando desativado, apenas o elemento de código em si é adicionado ao mapa. Para reverter esse comportamento para apenas um arrastar e soltar ação, pressione e segure o **CTRL** enquanto você arrasta os elementos de código para o mapa de chave.<br /><br /> O Visual Studio adiciona elementos de código para os elementos de nível superior de código em sua seleção. Para ver se um elemento de código contém outros elementos de código, mova o ponteiro do mouse sobre o elemento de código para que apareça na divisa (seta para baixo). Escolha na divisa para expandir o elemento de código. Para expandir todos os elementos de código, pressione **CTRL**+**um** para selecionar todos os elementos, abra o menu de atalho para o mapa e escolha **grupo**, **expandir** . Este comando não estará disponível se expandir todos os grupos deve produzir um mapa inutilizável ou causar problemas de memória insuficiente.|  
|Elementos de código relacionados a elementos de código no mapa.|Clique o **Mostrar relacionados** botão na barra de ferramentas de mapa de código e escolha o tipo de itens relacionados que lhe interessam.<br /><br /> - ou -<br /><br /> Abra o menu de atalho para o elemento de código. Escolha uma da **Mostrar...**  itens no menu, dependendo do tipo de relação de seu interesse. Por exemplo, você pode ver os itens que faça referência ao item atual, os itens que referenciam o item atual, os tipos base e derivados para classes, chamadores de método e que contém classes, namespaces e assemblies.<br /><br /> Para obter mais detalhes, consulte [neste tópico](../modeling/map-dependencies-across-your-solutions.md).|  
|Assemblies do .NET compilados (. dll ou .exe) ou binários.|Arraste os assemblies ou binários de fora do Visual Studio para um mapa.<br /><br /> Você pode arrastar do Windows Explorer ou do Explorador de arquivos somente se você estiver executando no mesmo nível de permissões de controle de acesso de usuário (UAC) ele e o Visual Studio. Por exemplo, se o UAC estiver ativado e você estiver executando o Visual Studio como administrador, o Windows Explorer ou do Explorador de arquivos bloqueará a operação de arrastar.|  
  
###  <a name="AddNodes"></a>   
##### <a name="add-a-link-between-existing-code-elements"></a>Adicionar um link entre os elementos de código existentes  
  
1.  Selecione o elemento de código fonte. Uma barra de ferramentas é exibida acima do elemento de código.  
  
     ![Barra de ferramentas de gráfico de dependência](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")  
  
2.  Na barra de ferramentas, escolha o ícone primeiro, **criar novo link deste nó para que qualquer nó que você clicar em Avançar**.  
  
3.  Selecione o elemento de código de destino. Aparecerá um link entre os elementos de código de dois.  
  
 \- ou -  
  
1.  Selecione o elemento de código fonte no mapa.  
  
2.  Se você tiver um mouse instalado, mova o ponteiro do mouse fora dos limites do mapa.  
  
3.  Abra o menu de atalho do elemento de código e escolha **editar**, **adicionar**, **Link genérico**.  
  
4.  Guia para e selecione o elemento de código de destino para o link.  
  
5.  Pressione **retornar**.  
  
###  <a name="AddComments"></a>   
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Adicionar um comentário a um nó existente no mapa  
  
1.  Selecione o elemento de código. Uma barra de ferramentas é exibida acima dele.  
  
     ![Barra de ferramentas de gráfico de dependência](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")  
  
2.  Na barra de ferramentas, escolha o ícone de terceiro, **criar um novo nó de comentário com um novo link para o nó selecionado**.  
  
     \- ou -  
  
     Abra o menu de atalho para o elemento de código e escolha **editar**, **novo comentário**.  
  
3.  Digite os comentários. Para o tipo em uma nova linha, pressione **SHIFT** + **retornar**.  
  
##### <a name="add-a-comment-to-the-map-itself"></a>Adicione um comentário para o mapa propriamente dito  
  
1.  Abra o menu de atalho para o mapa e escolha **editar**, **novo comentário**.  
  
2.  Digite os comentários. Para o tipo em uma nova linha, pressione **SHIFT** + **retornar**.  
  
###  <a name="RenameNodes"></a>   
##### <a name="rename-a-code-element-or-link"></a>Renomear um elemento de código ou link  
  
1.  Selecione o elemento de código ou o link que você deseja renomear.  
  
2.  Pressione **F2**, ou abra o menu de atalho e escolha **editar**, **Renomear**.  
  
3.  Quando aparecer a caixa de edição no mapa, renomeie o elemento de código ou o link.  
  
     \- ou -  
  
4.  Abra o menu de atalho e escolha **editar**, **propriedades**.  
  
5.  Editar o **rótulo** propriedade na janela Propriedades do Visual Studio.  
  
##### <a name="remove-a-code-element-or-link-from-the-map"></a>Remover um elemento de código ou link de mapa  
  
1.  Selecione o elemento de código ou link e pressione a **excluir** chave.  
  
     \- ou -  
  
     Abra o menu de atalho para o elemento de código ou link e escolha **editar**, **remover**.  
  
2.  Se o elemento ou o link é parte de um grupo, o **filhos buscar novamente** botão ![buscar novamente filhos ícone](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") aparece dentro do grupo. Clique aqui para recuperar os links e elementos ausentes.  
  
-   Você pode remover os elementos de código e links de um mapa sem afetar o código subjacente. Quando você excluí-los, suas definições serão removidas do arquivo de DGML (.dgml).  
  
-   Mapas criados por meio da edição de DGML, pela adição de elementos de código indefinido ou usando algumas versões anteriores do Visual Studio, não dão suporte a esse recurso.  
  
##### <a name="flag-a-code-element-for-follow-up"></a>Sinalizador de um elemento de código para acompanhamento  
  
1.  Selecione o elemento de código ou link que você deseja sinalizar para acompanhamento.  
  
2.  Abra o menu de atalho e escolha **editar**, **sinalizador para acompanhamento**.  
  
-   Por padrão, o elemento de código obtém um plano de fundo vermelho. Considere [adicionando um comentário](#AddComments) a ele com as informações de acompanhamento apropriadas.  
  
-   Alterar a cor de plano de fundo do elemento ou limpar o sinalizador de acompanhamento, escolhendo **editar**, **outras cores de sinalizador**.  
  
##  <a name="ChangeStyleCodeOrLink"></a>Alterar o estilo de um elemento de código ou link  
 Você pode alterar os ícones em elementos de código e as cores dos elementos de código e links usando cores e ícones predefinidos. Por exemplo, você pode escolher uma cor para realçar os elementos de código e links que têm uma certa categoria ou propriedade. Isso permite identificar e se concentrar em áreas específicas do mapa. Você pode especificar cores e ícones personalizados, editando o arquivo de .dgml do mapa. consulte [mapeia Personalizar código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Para aplicar uma cor predefinida ou um ícone para elementos de código ou links com uma certa categoria ou propriedade  
  
1.  Na barra de ferramentas do mapa, escolha **legenda**.  
  
2.  No **legenda** caixa, veja se a categoria de elemento de código ou propriedade já aparece na lista.  
  
3.  Se a lista não inclui a categoria ou propriedade, escolha  **+**  no **legenda** caixa e, em seguida, escolha **propriedade nó**, **categoria de nó** , **Vincular propriedade**, ou **vincular categoria**. Em seguida, escolha a categoria ou propriedade. A categoria ou propriedade aparece agora o **legenda** caixa.  
  
    > [!NOTE]
    >  Para criar e atribuir uma categoria ou uma propriedade a um elemento de código, você pode editar arquivo de .dgml do mapa. consulte [mapeia Personalizar código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
4.  No **legenda** caixa, clique no ícone próximo a categoria ou propriedade que você adicionou ou você deseja alterar.  
  
5.  Use a tabela a seguir para selecionar o estilo que você deseja alterar:  
  
    |**Para alterar o**|**Choose**|  
    |-----------------------|----------------|  
    |Cor do plano de fundo|**Tela de Fundo**|  
    |Cor do contorno|**Traço**|  
    |Cor do texto (uma letra "f" é exibida para mostrar o resultado)|**Em primeiro plano**|  
    |Ícone|**Ícones**|  
  
     O **seletor de cores definido** ou **ícone Definir seletor** caixa de diálogo é exibida para que você selecione uma cor ou ícone.  
  
6.  No **seletor de cores definido** ou **ícone Definir seletor** caixa de diálogo, siga um destes procedimentos:  
  
    |**Para aplicar um**|**Execute estas etapas**|  
    |--------------------|-----------------------------|  
    |Conjunto de cores ou ícones|Abra o **selecionar cor** (ou **ícone**) **definir** lista. Selecione um conjunto de ícones ou cores.|  
    |Cor específica ou um ícone|Abra a categoria ou a lista de valores da propriedade. Selecione uma cor ou ícone.|  
  
    > [!NOTE]
    >  Você pode reorganizar, excluir ou desativar temporariamente os estilos de **legenda** caixa. Consulte [editar a caixa legenda](#ModifyLegend).  
  
##  <a name="ModifyLegend"></a>Editar caixa de legenda  
 Você pode reorganizar, excluir ou desativar temporariamente os estilos de **legenda** caixa:  
  
1.  Abra o menu de atalho para um estilo de **legenda** caixa.  
  
2.  Realize uma das seguintes tarefas:  
  
    |**To**|**Choose**|  
    |------------|----------------|  
    |Desativar o elemento de código|**Desabilitar**|  
    |Excluir o elemento de código|**Excluir**|  
    |Mover o estilo para cima|**Mover para cima**|  
    |Mover o elemento de código para baixo|**Mover para baixo**|  
  
##  <a name="CopyLegend"></a>Estilos de cópia a partir de um mapa para outro  
  
1.  Verifique se o **legenda** caixa aparece no mapa de origem. Se não estiver visível, na barra de ferramentas do mapa, clique em **legenda**.  
  
2.  Abra o menu de atalho para o **legenda** caixa. Escolha **copiar legenda**.  
  
3.  Cole a legenda para o mapa de destino.  
  
##  <a name="MergeMaps"></a>Mapas de códigos de mesclagem  
 Você pode mesclar mapas, copiando e colando os elementos de código entre mapas. Se os identificadores de elemento de código correspondem, funções de elementos de código de colá-lo como uma operação de mesclagem. Para facilitar essa tarefa, coloque todos os assemblies ou binários que você deseja visualizar na mesma pasta, para que o caminho completo de cada assembly ou binário é o mesmo para cada mapa que você deseja mesclar.  
  
 Como alternativa, você pode arrastar esses assemblies ou binários para o mesmo mapa dessa pasta.  
  
## <a name="see-also"></a>Consulte também  
 [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)   
 [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Encontrar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Personalizar mapas de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)   
 [Referência DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
