---
title: "Cenário: Alterar o design usando visualização e modelagem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: "61"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: e6ffb17164bf49cb585d9fd67dd99c833a805411
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Cenário: alterar o design usando visualização e modelagem
Certifique-se de que o sistema de software atenda às necessidades de usuários usando a visualização e modelagem de ferramentas no Visual Studio.
Use ferramentas como mapas de código, diagramas de dependência e diagramas de classe para:  
  
 Para ver quais versões do Visual Studio oferecem suporte a cada ferramenta, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
-   Esclarecer os requisitos e os processos de negócios dos usuários.  
  
-   Visualize e explore o código existente.  
  
-   Descrevem as alterações em um sistema existente.  
  
-   Verifique se o sistema atende aos seus requisitos.  
  
-   Manter o código consistente com o design.  
  
 Este passo a passo:  
  
-   Descreve como essas ferramentas podem se beneficiar seu projeto de software.  
  
-   Mostra como você pode usar essas ferramentas, independentemente sua abordagem de desenvolvimento, com um cenário de exemplo.  
  
 Para obter mais informações sobre essas ferramentas e os cenários que oferecem suporte a eles, consulte:  
  
-   [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)  
  
-   [Visualizar código](../modeling/visualize-code.md)  
  
##  <a name="ScenarioOverview"></a>Visão geral do cenário  
 Este cenário descreve episódios dos ciclos de vida de desenvolvimento de software de duas empresas fictícias: uma refeição agora e Editora Zulu. Refeição agora fornece um serviço de distribuição baseado na Web refeição em Seattle. Os clientes podem solicitar refeições e pagar para eles no site da Web agora uma refeição. Os pedidos são enviados para o restaurante local apropriado para entrega. A Editora Zulu, uma empresa em Nova York, executa várias empresas off e na Web. Por exemplo, eles executarem um site da Web onde os clientes podem lançar revisões do restaurante.  
  
 Zulu recentemente adquirido uma refeição agora e deseja fazer as seguintes alterações:  
  
-   Integre seus sites da Web, adicionando recursos de análise do restaurante a refeição agora.  
  
-   Substitua sistema de pagamento de uma refeição agora por do Zulu.  
  
-   Expanda o serviço agora uma refeição toda a região.  
  
 Agora uma refeição usa SCRUM e programação extrema. Eles têm cobertura de teste muito alto e código muito pouco sem suporte. Minimizar os riscos por criando pequeno, mas versões de trabalho do sistema e, em seguida, adicionando funcionalidade incrementalmente. Eles desenvolverem seu código em curtas e frequentes iterações. Isso permite que eles adotar a alteração com confiança, refatorar o código com frequência e evitar "adiantado design grande".  
  
 Zulu mantém um conjunto muito maior e mais complexo de sistemas, alguns dos quais são mais de 40 anos de idade. Eles são muito cuidados ao fazer alterações devido à complexidade e escopo de código herdado. Sigam um processo de desenvolvimento mais rigoroso, preferindo para criar soluções detalhadas e documentar o design e as alterações que ocorrem durante o desenvolvimento.  
  
 Ambas as equipes usam diagramas de modelagem no Visual Studio para ajudar a desenvolver sistemas que atendam às necessidades dos usuários. Eles usam o Team Foundation Server junto com outras ferramentas para ajudar a planejar, organizar e gerenciar seus trabalhos.  
  
 Para obter mais informações sobre como Team Foundation Server, consulte:  
  
-   [Planejar e acompanhar um trabalho](#PlanningTracking)  
  
-   [Testes, validação e verificação do código atualizado](#TestValidateCheckInCode)  
  
##  <a name="ModelingDiagramsTools"></a>Funções de arquitetura e modelagem diagramas no desenvolvimento de Software  
 A tabela a seguir descreve as funções que podem executar essas ferramentas durante vários e vários estágios do ciclo de vida de desenvolvimento de software:  
  
||**Requisitos de usuário de modelagem**|**Modelagem de processos de negócios**|**Design e a arquitetura do sistema**|**Visualização de código e exploração**|**Verificação**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagrama de linguagem específica de domínio (DSL)|Sim|Sim|Sim|||  
|Diagrama de dependência, validação de camada|||Sim|Sim|Sim|  
|Mapa de código|||Sim|Sim|Sim|  
|Designer de classe (base)||||Sim||  
  
Para desenhar os diagramas de dependência, você deve criar um projeto de modelagem como parte de uma solução existente ou um novo. Esses diagramas devem ser criados no projeto de modelagem.
Itens em diagramas de dependência estão localizados no projeto de modelagem, mas elas não são armazenadas no modelo comum. Mapas de código e diagramas de classe .NET criados a partir de código existem fora do projeto de modelagem.  
  
 Consulte:  
  
-   [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
-   [SDK de Modelagem para Visual Studio – linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 Ambas as equipes também usam a validação de dependência para certificar-se de que o código em desenvolvimento permaneça consistente com o design.  
  
 Consulte:  
  
-   [Manter o código consistente com o Design](#ValidatingCode)  
  
-   [Descreve a arquitetura lógica: diagramas de dependência](#DescribeLayers)  
  
-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)  
  
    > [!NOTE]
    >  Algumas versões do Visual Studio oferecem suporte a versões somente leitura de mapas de código e validação de dependência para visualização e modelagem. Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="UnderstandingCommunicating"></a>Compreender e comunicar informações sobre o sistema  
 Não há nenhuma ordem prescrita para usar o Visual Studio para que possa usá-los como elas se ajustarem com suas necessidades ou abordagem de modelagem diagramas. Geralmente, as equipes rever seus modelos iterativamente e frequentemente em todo o projeto. Cada diagrama oferece vantagens específicas para ajudá-lo a entender, descrever e se comunicar diferentes aspectos do sistema em desenvolvimento.  
  
 Agora uma refeição e Zulu se comunicar entre si e com os participantes do projeto por meio de diagramas como idioma comum. Por exemplo, uma refeição agora usa diagramas para executar estas tarefas:  
  
-   Visualize código existente.  
  
-   Comunicar com Zulu histórias de usuários novos ou atualizados.  
  
-   Identificar as alterações necessárias para dar suporte a histórias de usuários novos ou atualizados.  
  
 Zulu usa diagramas para executar estas tarefas:  
  
-   Saiba mais sobre o processo de negócios refeição agora.  
  
-   Entenda o design do sistema.  
  
-   Se comunicar com uma refeição agora sobre os requisitos de usuário novo ou atualizado.  
  
-   Atualizações de documento para o sistema.  
  
 Os diagramas são integrados com o Team Foundation Server para que as equipes podem planejar, gerenciar e controlar seu trabalho mais facilmente. Por exemplo, usar modelos para identificar casos de teste e tarefas de desenvolvimento e para estimar o seu trabalho. Links de Zulu Team Foundation Server itens a elementos de modelo de trabalho para que eles podem monitorar o andamento e certifique-se de que o sistema atende aos requisitos dos usuários. Por exemplo, eles vinculem casos de uso para itens de trabalho de caso de teste para que eles possam ver que os casos de uso são preenchidos quando todos os testes passarem.  
  
 Antes que as equipes de check-in de suas alterações, eles validam o código com o design e os testes executando compilações que incluem a validação de dependência e testes automatizados. Isso ajuda a garantir que o código atualizado não entram em conflito com o design e anteriormente interromper a funcionalidade de trabalho.  
  
 Consulte:  
  
-   [Identificar alterações no sistema existente](#DeterminingChanges)  
  
-   [Manter o código consistente com o design](#ValidatingCode)  
  
-   [Dicas gerais para criar e usar modelos](#GeneralTips)  
  
-   [Planejar e acompanhar um trabalho](#PlanningTracking)  
  
-   [Testes, validação e verificação do código atualizado](#TestValidateCheckInCode)  

###  <a name="DeterminingChanges"></a>Identificar alterações no sistema existente  
 Agora uma refeição deve estimar o custo de atender o novo requisito. Isso depende em parte quanto esta alteração irá afetar outras partes do sistema. Para compreender isso, um dos desenvolvedores agora uma refeição cria esses mapas e diagramas de código existente:  
  
|**Mapa ou diagrama**|**programas**|  
|------------------------|---------------|  
|*Mapa de código*<br /><br /> Consulte:<br /><br /> -   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personalizar mapas de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dependências e as outras relações no código.<br /><br /> Por exemplo, uma refeição agora pode começar revisando os mapas de código de assembly para obter uma visão geral de assemblies e suas dependências. Eles podem detalhar os mapas para explorar os namespaces e classes desses assemblies.<br /><br /> Agora uma refeição também pode criar mapas para explorar a áreas específicas e outros tipos de relações no código. Eles usam o Gerenciador de soluções para localizar e selecionar as áreas e relações de seu interesse.|  
|*Diagrama de classe base*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes no código|  
  
 Por exemplo, o desenvolvedor cria um mapa de código. Ela ajusta seu escopo para se concentrar em áreas que serão afetadas do novo cenário. Essas áreas são selecionadas e realçadas no mapa:  
  
 ![Gráfico de dependência de Namespace](../modeling/media/namespace_reviewsystem.png "Namespace_ReviewSystem")  
  
 **Mapa de código de Namespace**  
  
 O desenvolvedor expande os namespaces selecionados para ver suas classes, métodos e relações:  
  
 ![Gráfico de dependência de namespace expandido](../modeling/media/dep_reviewsystem.png "Dep_ReviewSystem")  
  
 **Mapa de código namespace expandido com links entre grupos visíveis**  
  
 O desenvolvedor examina o código para localizar o afetados classes e métodos. Para ver os efeitos de cada alteração medida que eles, gerar código mapeia após cada alteração. Consulte [Visualizar código](../modeling/visualize-code.md).  
  
 Para descrever as alterações a outras partes do sistema, como componentes ou interações, a equipe pode desenhar esses elementos em quadros de comunicações. Eles também podem desenhar os diagramas a seguir no Visual Studio para que os detalhes podem ser capturados, gerenciados e entendidos por ambas as equipes:  
  
|**Diagramas**|**Descreve**|  
|------------------|-------------------|  
|*Diagrama de classe base*<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes no código.|  
  
###  <a name="ValidatingCode"></a>Manter o código consistente com o Design  
 Refeição agora deve se certificar de que o código atualizado permanece consistente com o design. Eles criar diagramas de dependência que descrevem as camadas de funcionalidade no sistema, especifique as dependências permitidas entre os artefatos de solução-las e associar a essas camadas.  
  
|**Diagrama**|**Descreve**|  
|-----------------|-------------------|  
|*Diagrama de dependência*<br /><br /> Consulte:<br /><br /> -   [Criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|A arquitetura lógica do código.<br /><br /> Um diagrama de dependência para organizar e mapeia os artefatos em um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução abstrair grupos chamados *camadas*. Essas camadas identificam as funções, tarefas ou funções que executam esses artefatos no sistema.<br /><br /> Diagramas de camada são úteis para descrever o design desejado do sistema e validação de código em evolução em relação a esse design.<br /><br /> Para criar camadas, arraste itens do Gerenciador de soluções, mapas de código, modo de exibição de classe e Pesquisador de objetos. Para desenhar as novas camadas, use a caixa de ferramentas ou clique superfície do diagrama.<br /><br /> Para exibir as dependências existentes, clique com botão direito a superfície do diagrama de camada e, em seguida, clique em **dependências gerar**. Para especificar dependências pretendidas, desenhe novas dependências.|  
  
 Por exemplo, o diagrama de dependência a seguir descreve as dependências entre camadas e o número de artefatos que estão associados a cada camada:  
  
 ![Diagrama de dependência do sistema de pagamento integrada](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagrama de dependência**  
  
 Para certificar-se de que está em conflito com o design não ocorra durante o desenvolvimento de código, os usos de equipes validação de dependência em compilações que são executados no Team Foundation Build. Eles também criar uma tarefa MSBuild personalizada para exigir a validação de dependência em suas operações de check-in. Eles usam a criar relatórios para coletar erros de validação.  
  
 Consulte:  
  
-   [Definir o processo de compilação](http://msdn.microsoft.com/Library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [Usar um processo de build de check-in restrito para validar as alterações](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [Personalizar o modelo de processo de compilação](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="GeneralTips"></a>Dicas gerais para criar e usar modelos  
  
-   A maioria dos diagramas consistem em nós que são conectados por linhas. Para cada tipo de diagrama, a caixa de ferramentas fornece diferentes tipos de nós e linhas.  
  
     Para abrir a caixa de ferramentas no **exibição** menu, clique em **caixa de ferramentas**.  
  
-   Para criar um nó, arraste-o na caixa de ferramentas para o diagrama. Determinados tipos de nós devem ser arrastados para nós existentes. Por exemplo, em um diagrama de componente, uma nova porta deve ser adicionada a um componente existente.  
  
-   Para criar uma linha ou uma conexão, clique na ferramenta apropriada na caixa de ferramentas, clique no nó de origem e, em seguida, clique no nó de destino. Algumas linhas podem ser criadas somente entre determinados tipos de nós. Quando você move o ponteiro sobre uma possível origem ou destino, o ponteiro indica se é possível criar uma conexão.  
  
###  <a name="PlanningTracking"></a>Planejar e acompanhar um trabalho  
 Diagramas de modelagem do Visual Studio são integrados com o Team Foundation Server para que você pode planejar, gerenciar e controlar o trabalho mais facilmente. Ambas as equipes usam modelos para identificar casos de teste e tarefas de desenvolvimento e para estimar o seu trabalho. Zulu cria e itens a elementos de modelo, como casos de uso ou componentes de trabalho de links Team Foundation Server. Isso ajuda a monitorar o andamento e rastrear o seu trabalho para os requisitos dos usuários. Isso ajuda a garantir que as alterações continuem a atender esses requisitos.  
  
 Como seus trabalhos em andamento, a atualização de equipes itens de trabalho para refletir a hora em que eles gastam em suas tarefas. Eles também monitorar e relatar o status em seu trabalho, usando os seguintes recursos do Team Foundation Server:  
  
-   Diário *relatórios de progresso* que mostram se eles concluirá o trabalho planejado no tempo esperado. Elas geram outros relatórios semelhantes do Team Foundation Server para acompanhar o andamento de bugs.  
  
-   Um *planilha iteração* que usa o Microsoft Excel para ajudar a equipe a monitorar e balancear a carga de trabalho entre seus membros. Esta planilha está vinculada ao Team Foundation Server e fornece o foco para discussão durante suas reuniões regulares de andamento.  
  
-   Um *painel desenvolvimento* que usa o Office Project para manter a equipe informada sobre informações importantes do projeto.  
  
 Consulte:  
  
-   [Acompanhar o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
-   [Gráficos, painéis e relatórios para o Visual Studio ALM](http://msdn.microsoft.com/Library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
-   [Criar sua lista de pendências e tarefas usando o Project](http://msdn.microsoft.com/Library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="TestValidateCheckInCode"></a>Testes, validação e verificação do código  
 Como as equipes de executar cada tarefa, eles Verifique seu código no controle de versão do Team Foundation e recebem lembretes do Team Foundation Server, caso eles esqueçam. Antes de Team Foundation Server aceita seus check-ins, as equipes de executam testes de unidade e validação de dependência para verificar o código em relação a seus casos de teste e o design. Usar o Team Foundation Server para executar compilações, testes de unidade automatizados e validação de dependência regularmente. Isso ajuda a garantir que o código atenda aos seguintes critérios:  
  
-   Ele funciona.  
  
-   Ele não interrompido anteriormente código funcional.  
  
-   Ele não está em conflito com o design.  
  
 Refeição agora tem uma grande coleção de testes automatizados, que Zulu pode reutilizar porque quase todo ainda se aplicam. Zulu também pode criar esses testes e adicionar novos para cobrir a nova funcionalidade. Ambos também usam o Visual Studio para executar testes manuais.  
  
 Para certificar-se de que o código está em conformidade com o design, as equipes de configurar suas compilações no Team Foundation Build para incluir validação de dependência. Se ocorrerem conflitos, um relatório é gerado com os detalhes.  
  
 Consulte:  
  
-   [Testando o aplicativo](https://www.visualstudio.com/docs/test/overview)  
  
-   [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)  
  
-   [Usar controle de versão](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
-   [Compilar o aplicativo](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
##  <a name="UpdatingSystem"></a>Atualizando a sistema usando visualização e modelagem  
 Zulu e agora uma refeição devem integrar seus sistemas de pagamento. As seções a seguir mostram que os diagramas de modelagem no Visual Studio ajudá-los a realizar esta tarefa:  
  
-   [Visualizar código existente: Mapas de código](#VisualizeCode)  
  
-   [Definir um glossário de tipos: diagramas de classe](#DefineClasses)  
  
-   [Descreve a arquitetura lógica: diagramas de dependência](#DescribeLayers)  
  
 Consulte:  
  
-   [Visualizar código](../modeling/visualize-code.md)  
  
-   [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)  
  
-   [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)  
 
###  <a name="VisualizeCode"></a>Visualizar código existente: Mapas de código  
 Mapas de código mostram a organização atual e as relações no código. Itens são representados por *nós* no mapa, e as relações são representadas por *links*. Mapas de código podem ajudá-lo a realizar os seguintes tipos de tarefas:  
  
-   Explore o código não familiar.  
  
-   Compreenda onde e como uma alteração proposta pode afetar o código existente.  
  
-   Localize áreas de complexidade, dependências naturais ou padrões ou outras áreas que podem se beneficiar de melhoria.  
  
 Por exemplo, uma refeição agora deve estimar o custo de atualização de componente PaymentProcessing. Isso depende em parte quanto esta alteração irá afetar outras partes do sistema. Para compreender isso, um dos desenvolvedores refeição agora gera mapas de código do código e ajusta o foco de escopo em áreas que podem ser afetados pela alteração.  
  
 O mapa a seguir mostra as dependências entre a classe PaymentProcessing e outras partes do sistema refeição agora, que aparecem selecionadas:  
  
 ![Gráfico de dependência para o sistema de pagamento agora uma refeição](../modeling/media/dep_dnpayment.png "Dep_DNPayment")  
  
 **Mapa de código para o sistema de pagamento refeição agora**  
  
 O desenvolvedor explora o mapa, expandindo a classe PaymentProcessing e selecionando a seus membros para ver as áreas que são potencialmente afetadas:  
  
 ![Métodos PaymentProcessing e dependências](../modeling/media/depgraph_expandeddn.png "DepGraph_ExpandedDN")  
  
 **Métodos dentro da classe PaymentProcessing e suas dependências**  
  
 Gerar o mapa a seguir para o sistema de pagamento Zulu inspecionar suas classes, métodos e as dependências. A equipe vê que o sistema Zulu também pode exigir o trabalho para interagir com as outras partes do refeição agora:  
  
 ![Gráfico de dependência para o sistema de pagamento Zulu](../modeling/media/depgraph_lucernepay.png "DepGraph_LucernePay")  
  
 **Mapa de código para o sistema de pagamento Zulu**  
  
 Ambas as equipes trabalham juntos para determinar as alterações que são necessárias para integrar os dois sistemas. Decidir refatorar parte do código para que ela será mais fácil de atualizar. A classe PaymentApprover será movido para o namespace DinnerNow.Business e exigirá que alguns novos métodos. As classes agora uma refeição que lidam com transações terá seu próprio namespace. As equipes de criar e usam itens de trabalho para planejar, organizar e acompanhar seu trabalho. Eles vincular os itens de trabalho em que é útil em elementos de modelo.  
  
 Após a reorganização de código, as equipes de geram um novo mapa de código para ver a estrutura atualizada e relações:  
  
 ![Gráfico de dependência com o código reorganizado](../modeling/media/depgraph_integrated.png "DepGraph_Integrated")  
  
 **Mapa de códigos com o código reorganizado**  
  
 Este mapa mostra a classe PaymentApprover agora está no namespace DinnerNow.Business e tem alguns novos métodos. As classes de transação agora uma refeição agora tem seu próprio namespace PaymentSystem, o que torna mais fácil de lidar com esse código mais tarde.  
  
#### <a name="creating-a-code-map"></a>Criar um mapa de código  
  
-   Para obter uma visão geral rápida do código-fonte, siga estas etapas para gerar um mapa de código:  
  
     Sobre o **arquitetura** menu, clique em **gerar mapa de código para solução**.  
  
     Para obter uma visão geral rápida do código compilado, criar um mapa de código em branco e, em seguida, arraste os arquivos de assembly ou arquivos binários para a superfície de mapa.  
  
-   Para explorar os itens de solução ou de código específico, use o Gerenciador de soluções para selecionar itens e as relações que você deseja visualizar. Você pode gerar um novo mapa ou adicionar itens selecionados a um mapa existente. Consulte [mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Para ajudá-lo a explorar o mapa, reorganizar o layout para que ele atenda os tipos de tarefas que você deseja executar.  
  
     Por exemplo, para visualizar as camadas no código, selecione um layout de árvore. Consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Resumo: Os pontos fortes dos mapas de código  
 Mapas de código ajudarão-lo:  
  
-   Saiba mais sobre a organização e as relações no código existente.  
  
-   Identificar áreas que podem ser afetadas por uma alteração proposta.  
  
-   Localize áreas de complexidade, padrões, camadas ou outras áreas que você possa melhorar para facilitar a manter, alterar e reutilizar o código.  
  
#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas  
  
|**Diagrama**|**Descreve**|  
|-----------------|-------------------|  
|Diagrama de dependência|A arquitetura lógica do sistema. Use a validação de dependência para certificar-se de que o código permanece consistente com o design.<br /><br /> Para ajudá-lo a identificar dependencys existentes ou dependencys pretendidas, crie um mapa de código e agrupar itens relacionados. Para criar um diagrama de dependência, consulte:<br /><br /> -   [Criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)|  
|Diagrama de classe (base)|Classes existentes no código para um projeto específico.<br /><br /> Para visualizar e modificar uma classe existente no código, use o Designer de classe.<br /><br /> Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
###  <a name="DefineClasses"></a>Definir um glossário de tipos: diagramas de classe  
 Diagramas de classe definem as entidades, termos ou conceitos que participam do sistema e suas relações uns com os outros. Por exemplo, você pode usar esses diagramas durante o desenvolvimento para descrever os atributos e operações para cada classe, independentemente da linguagem de implementação ou estilo.  
  
 Para ajudar a Zulu descrever e discutir as entidades que participam no caso de uso de pagamento de processo, eles desenhar o diagrama de classe a seguir:  
  
 ![Processar entidades de pagamento no diagrama de classe](../modeling/media/uml_payentities.png "UML_PayEntities")  
  
 **Entidades de pagamento de processo em um diagrama de classe**  
  
 Este diagrama mostra que um cliente pode ter muitos pedidos e formas de pagamento para ordens diferentes. BankAccount e CreditCard herdam de pagamento.  
  
 Durante o desenvolvimento, Zulu usa o diagrama de classe a seguir para descrever e discutir os detalhes de cada classe:  
  
 ![Processar os detalhes de entidade de pagamento em um diagrama de classe](../modeling/media/uml_payment.png "UML_Payment")  
  
 **Detalhes de pagamento do processo no diagrama de classe**  
    
#### <a name="drawing-a-class-diagram"></a>Desenho de um diagrama de classe  
 Um diagrama de classe tem os seguintes recursos principais:  
  
-   Tipos, como classes, interfaces e enumerações:  
  
    -   Um *classe* é a definição de objetos que compartilham características específicas de comportamentos ou estruturais.  
  
    -   Um *interface* define uma parte do comportamento visível externamente de um objeto.  
  
    -   Um *enumeração* é um classificador que contém uma lista de valores literais.  
  
-   *Atributos* são valores de um determinado tipo que descrevem cada instância de um *classificador*. Um classificador é um nome geral para tipos, componentes, casos de uso e até mesmo atores.  
  
-   *Operações* são métodos ou funções que podem ser executadas por instâncias de um classificador.  
  
-   Um *associação* indica algum tipo de relação entre dois classificadores.  
  
    -   Um *agregação* é uma associação que indica uma propriedade compartilhada entre classificadores.  
  
    -   Um *composição* é uma associação que indica uma relação de parte de inteiro entre classificadores.  
  
     Para mostrar agregações ou composições, defina o **agregação** propriedade em uma associação. **Compartilhado** mostra agregações e **composto** mostra composições.  
  
-   Um *dependência* indica alterando a definição de um classificador pode alterar a definição de outro classificador.  
  
-   Um *generalização* indica que uma classificação específica herda parte de sua definição de um classificador geral. Um *realização* indica que uma classe implemente as operações e atributos oferecidos por uma interface.  
  
     Para criar essas relações, use o **herança** ferramenta. Como alternativa, uma realização pode ser representada como um *pirulito*.  
  
-   *Pacotes* são grupos de classificadores, associações, linhas de vida, componentes e outros pacotes. *Importação* relações indicam que um pacote inclui todas as definições de outro pacote.  
  
 Como ponto de partida para explorar e discutir as classes existentes, você pode usar o Designer de classe para criar diagramas de classe a partir do código.  
  
-   [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Resumo: Os pontos fortes de diagramas de classe  
 Diagramas de classe ajudarão-lo a definir:  
  
-   Um Glossário comum de termos para usar ao abordar as necessidades dos usuários e entidades que participam do sistema. Consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
-   Tipos que são usados por partes do sistema, como componentes, independentemente de sua implementação. Consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).  
  
-   Relações, como dependências entre tipos. Por exemplo, você pode mostrar que um tipo pode ser associado a várias instâncias de outro tipo.  
  
#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas  
  
|**Diagrama**|**Descrição**|  
|-----------------|---------------------|  
|Diagrama de dependência|Defina a arquitetura lógica do sistema, como ele se relaciona com classes.<br /><br /> Use a validação de dependência para certificar-se de que o código permanece consistente com o design.<br /><br /> Consulte:<br /><br /> -   [Criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|  
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para identificar seus métodos, classes e suas relações, crie um mapa de código que mostra esses elementos.<br /><br /> Consulte:<br /><br /> -   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="DescribeLayers"></a>Descreve a arquitetura lógica: diagramas de dependência  
 Diagramas de dependência descrevem a arquitetura lógica de um sistema, organizando os artefatos em sua solução em grupos abstratos, ou *camadas*. Artefatos podem ser muitas coisas, como namespaces, projetos, classes, métodos e assim por diante. Camadas representam e descrevem as funções ou tarefas que executam os artefatos no sistema. Você também pode incluir validação de camada no build e as operações de verificação para certificar-se de que o código permanece consistente com seu design.  
  
 Para manter o código consistente com o design, uma refeição agora e Zulu usam o seguinte diagrama de dependência para validar o código, à medida que ele evolui:  
  
 ![Diagrama de dependência do sistema de pagamento integrada](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagrama de dependência para uma refeição agora integrado ao Zulu**  
  
 As camadas neste diagrama vincular os artefatos de solução uma refeição agora e Zulu correspondentes. Por exemplo, os links de camada de negócios para o namespace DinnerNow.Business e seus membros, que agora incluem a classe PaymentApprover. Os links de camada de acesso aos recursos para o namespace DinnerNow.Data. As setas ou *dependências*, especifique que a camada de negócios pode usar a funcionalidade na camada de acesso aos recursos. Assim como as equipes de atualizar seu código, validação de camada é executada regularmente para detectar conflitos, conforme elas ocorrem e ajuda as equipes de resolvê-los imediatamente.  
  
 As equipes trabalham em conjunto para integrar incrementalmente e os dois sistemas de teste. Primeiro verifique se PaymentApprover e o restante de uma refeição agora funcionam com uma outra com êxito antes de lidar com PaymentProcessing.  
  
 O mapa de código a seguir mostra as novo chamadas entre o refeição agora e PaymentApprover:  
  
 ![Gráfico de dependência atualizado com o sistema integrado](../modeling/media/depgraph_intsystem.png "DepGraph_IntSystem")  
  
 **Mapa de códigos com chamadas de método atualizado**  
  
 Agora uma refeição comentários depois que eles confirmam que o sistema funciona conforme o esperado, o código de PaymentProcessing. Os relatórios de validação de camada são limpos e o mapa de código resultante mostra que não há mais dependências PaymentProcessing existem:  
  
 ![Gráfico de dependência sem PaymentProcessing](../modeling/media/depgraph_nomore.png "DepGraph_NoMore")  
  
 **Mapa de código sem PaymentProcessing**  
  
#### <a name="drawing-a-dependency-diagram"></a>Desenho de um diagrama de dependência  
 Um diagrama de dependência tem os seguintes recursos principais:  
  
-   *Camadas* descrevem grupos lógicos de artefatos.  
  
-   Um *link* é uma associação entre uma camada e um artefato.  
  
     Para criar camadas de artefatos, arraste itens do Gerenciador de soluções, mapas de código, modo de exibição de classe ou Pesquisador de objetos. Para desenhar novas camadas e, em seguida, vinculá-las aos artefatos, use a caixa de ferramentas ou clique na superfície do diagrama para criar as camadas e, em seguida, arraste os itens para essas camadas.  
  
     O número em uma camada mostra o número de artefatos que estão vinculados à camada. Esses artefatos podem ser projetos, namespaces, classes, métodos e assim por diante. Quando você interpretar o número de artefatos em uma camada, lembre-se do seguinte:  
  
    -   Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.  
  
         Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.  
  
    -   Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.  
  
     Para ver os artefatos que estão vinculados a uma camada, clique com botão direito a dependência e, em seguida, clique em **Exibir Links** abrir **Explorer camada**.  
  
-   Um *dependência* indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa. Um *dependência bidirecional* indica que uma camada pode usar a funcionalidade em outra camada e vice-versa.  
  
     Para exibir as dependências existentes no diagrama de dependência, clique com botão direito a superfície do diagrama e, em seguida, clique em **dependências gerar**. Para descrever dependências pretendidas, desenhe novos.  
  
 Consulte:  
  
-   [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)  
  
-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)  
  
-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-dependency-diagrams"></a>Resumo: Os pontos fortes de diagramas de dependência  
 Diagramas de dependência ajudarão-lo:  
  
-   Descrevem a arquitetura lógica de um sistema de acordo com a funcionalidade de seus artefatos.  
  
-   Certifique-se de que o código em desenvolvimento está de acordo com o projeto especificado.  
  
#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas  
  
|**Diagrama**|**Descrição**|  
|-----------------|---------------------|  
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para criar camadas, gerar um mapa de código e, em seguida, agrupar os itens no mapa como camadas potenciais. Arraste os grupos do mapa para o diagrama de dependência.<br /><br /> Consulte:<br /><br /> -   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)|  
  
## <a name="external-resources"></a>Recursos externos  
  
|**Categoria**|**Links**|  
|------------------|---------------|  
|**Fóruns**|-   [Visualização do Visual Studio e ferramentas de modelagem](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visualização do Visual Studio e modelagem SDK (ferramentas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Consulte também  
 [Visualizar código](../modeling/visualize-code.md)   
 [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)   
 [Usar modelos de desenvolvimento ágil](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)   

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
