---
title: Usar modelos no processo de desenvolvimento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: get-started-article
helpviewer_keywords:
- UML, using models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4d8d9b5632831c1d336f359aa4e4468da1543c73
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2018
---
# <a name="use-models-in-your-development-process"></a>Usar modelos no processo de desenvolvimento

No Visual Studio, você pode usar um modelo para ajudá-lo a entender e alterar um sistema, aplicativo ou componente. Um modelo pode ajudá-lo a visualizar o mundo em que o sistema funciona, esclarecer necessidades dos usuários, definir a arquitetura do seu sistema, analisar o código e certifique-se de que seu código atende aos requisitos. Consulte [vídeo do Channel 9: arquitetura por meio da modelagem de melhorar](http://go.microsoft.com/fwlink/?LinkID=252078).

Para ver quais versões do Visual Studio oferecem suporte a cada tipo de modelo, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Modelos podem ajudá-lo de várias maneiras:

- Diagramas de modelagem de desenho o ajudará a esclarecer os conceitos envolvidos em requisitos de arquitetura e design de alto nível. Para obter mais informações, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).

- Trabalhando com modelos pode ajudá-lo a expor as inconsistências em requisitos.

- Comunicação com modelos ajuda você a se comunicar conceitos importantes menor maneira ambígua com idioma natural. Para obter mais informações, consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).

- Às vezes, você pode usar modelos para gerar o código ou outros artefatos, como documentos ou esquemas de banco de dados. Por exemplo, os componentes de modelagem do Visual Studio são gerados de um modelo. Para obter mais informações, consulte [gerar e configurar seu aplicativo de modelos de](../modeling/generate-and-configure-your-app-from-models.md).

Você pode usar modelos em uma ampla variedade de processos do extremo cerimônia agile para alta.

## <a name="use-models-to-reduce-ambiguity"></a>Use modelos para reduzir a ambiguidade

Linguagem de modelagem é menos ambígua de idioma natural e ele é projetado para expressar ideias normalmente necessárias durante o desenvolvimento de software.

Se o projeto tiver uma equipe pequena agile práticas a seguir, você pode usar modelos para ajudar a esclarecer histórias de usuários. Em conversas com o cliente sobre suas necessidades, a criação de um modelo pode gerar perguntas úteis muito mais rápido e em uma área maior do produto, que escrever código de pico ou protótipo.

Se seu projeto for grande e inclui as equipes em diferentes partes do mundo, você pode usar modelos para ajudar a se comunicar os requisitos e a arquitetura de forma muito mais eficiente do que no texto sem formatação.

Em ambos os casos criando um modelo de quase sempre resulta em uma redução significativa na inconsistências e ambiguidades. Frequentemente, participantes diferentes têm diferentes Noções básicas do mundo dos negócios em que o sistema funciona e frequentemente, os desenvolvedores diferentes têm diferentes Noções básicas de como funciona o sistema. Usando um modelo como o foco de uma discussão geral expõe essas diferenças. Para obter mais informações sobre como usar um modelo para reduzir as inconsistências, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).

## <a name="use-models-with-other-artifacts"></a>Usar modelos com outros artefatos

Um modelo não é por si só, uma especificação de requisitos ou uma arquitetura. É uma ferramenta para expressar alguns aspectos essas coisas mais claramente, mas não todos os conceitos necessários durante o design de software podem ser expressas. Os modelos, portanto, devem ser usados junto com outros meios de comunicação, como páginas do OneNote ou parágrafos, documentos do Microsoft Office, itens de trabalho em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)], ou notas na parede de espaço do projeto. O último item, além de todos os tipos de objeto podem ser vinculados a partes de elementos do modelo.

Outros aspectos da especificação que normalmente são usados junto com os modelos incluem o seguinte. Dependendo da escala e o estilo de seu projeto, você pode usar vários esses aspectos ou não usar nenhum:

- Histórias de usuários. Uma história de usuário é uma breve descrição, discutida com usuários e outros participantes, de um aspecto do comportamento do sistema que será entregue em uma das iterações do projeto. Uma história de usuário típico começa "o cliente será capaz de..." Uma história de usuário pode apresentar um grupo de casos de uso ou pode definir as extensões de casos de uso que foram desenvolvidos anteriormente. Definir ou estender os casos de uso ajuda a aumentar a história de usuário mais clara.

- Solicitações de alteração. Uma solicitação de alteração em um projeto mais formal é muito semelhante a uma história de usuário em um projeto agile. A abordagem agile trata todos os requisitos de como as alterações para o que foi desenvolvido em iterações anteriores.

- Use a descrição do caso. Um caso de uso representa uma forma em que um usuário interage com o sistema para atingir uma meta específica. Uma descrição completa inclui a meta principais e alternativas sequências de eventos e resultados excepcionais. Um diagrama de caso de uso ajuda a resumir e fornecem uma visão geral dos casos de uso.

- Cenários. Um cenário é uma descrição bastante detalhada de uma sequência de eventos mostrando como o sistema, os usuários e outros sistemas funcionam juntos para fornecer um valor para as partes interessadas. Ele pode assumir a forma de um slide show da interface do usuário ou um protótipo da interface do usuário. Ela descreve um caso de uso ou uma sequência de casos de uso.

- Glossário. Glossário de requisitos do projeto descreve as palavras com a qual os clientes discutem o mundo. Os modelos de requisitos e a interface do usuário também devem usar estes termos. Um diagrama de classe pode ajudar a esclarecer os relacionamentos entre a maioria destes termos. Criar os diagramas e glossário não apenas reduz confusão entre os desenvolvedores e usuários, mas também quase sempre expõe confusão entre os participantes de negócios diferente.

- Regras de negócio. Muitas regras de negócio podem ser expressos como restrições invariáveis em associações de atributos no modelo de classe de requisitos e restrições em diagramas de sequência.

- Design de alto nível. Descreve as principais partes e como elas se encaixam. Componente, sequência e diagramas de interface são uma parte importante de um design de alto nível.

- Padrões de design. Descrevem as regras de design que são compartilhadas entre as diferentes partes do sistema.

- Especificações de teste. Scripts de teste e os designs de código de teste podem fazer bom uso de diagramas de atividade e de sequência para descrever as sequências de etapas de teste. Testes de sistema devem ser expressa em termos de modelo de requisitos para que eles podem ser alterados facilmente quando os requisitos de alteração.

- Plano de projeto. O plano de projeto ou a lista de pendências define quando cada recurso será entregue. Você pode definir cada recurso informando quais casos de uso e ele implementa ou estende as regras de negócio. Você pode se referir a casos de uso e as regras de negócios diretamente no plano de, ou você pode definir um conjunto de recursos em um documento separado e usar os títulos de recurso no plano.

## <a name="use-models-in-iteration-planning"></a>Usar modelos no planejamento de iteração

Embora todos os projetos são diferentes em sua escala e a organização, um projeto típico é planejado como uma série de iterações de entre dois e seis semanas. É importante planejar suficiente iterações para permitir que os comentários de iterações anteriores a ser usado para ajustar o escopo e os planos para posteriores iterações.

Talvez você considere as seguintes sugestões úteis para ajudar a obter os benefícios de modelagem em um projeto iterativo.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Nítido conforme se aproxima de cada iteração

Como cada iteração abordagens, use modelos para ajudar a definir o que é entregue ao final da iteração.

- Modelo não tudo em detalhes nas iterações anteriores. Na primeira iteração, criar um diagrama de classe para os principais itens no glossário do usuário, faça um diagrama dos casos de uso principal e desenhe um diagrama dos principais componentes. Descreve qualquer uma dessas muitos detalhes, como os detalhes serão alteradas posteriormente no projeto. Use os termos definidos neste modelo para criar uma lista de recursos ou histórias de usuário principal. Atribua os recursos de iterações para aproximadamente equilibrar a carga de trabalho estimada em todo o projeto. Essas atribuições serão alterada posteriormente no projeto.

- Tente implementar versões simplificadas de todos os casos de uso mais importantes em uma iteração anterior. Estender os casos de uso em iterações posteriores. Essa abordagem ajuda a reduzir o risco de descoberta de uma falha nos requisitos ou a arquitetura muito tarde no projeto fazer nada sobre ele.

- No final de cada iteração, mantenha um workshop de requisitos para definir detalhes de requisitos ou histórias de usuário que serão desenvolvidas na próxima iteração. Convide usuários e participantes de negócios que podem decidir prioridades, bem como os desenvolvedores e testadores do sistema. Permitir três horas definir os requisitos para uma iteração de 2 semanas.

- O objetivo do workshop é para qualquer usuário concorda que será realizado ao final da próxima iteração. Use modelos como uma das ferramentas para ajudar a esclarecer os requisitos. A saída do workshop é uma lista de pendências de iteração: ou seja, as tarefas de uma lista de desenvolvimento em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] e testar pacotes no [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)].

- A fábrica de requisitos, sobre o design somente na medida, você precisa determinar as estimativas para as tarefas de desenvolvimento. Caso contrário, mantenha a discussão de comportamento do sistema que os usuários podem enfrentar diretamente. Manter o modelo de requisitos separado do modelo de arquitetura.

- Os participantes não técnicos geralmente não têm problemas Noções básicas sobre diagramas UML, com algumas diretrizes sobre você.

### <a name="link-model-to-work-items"></a>Modelo de link para itens de trabalho

Após a fábrica de requisitos, elaborar os detalhes do modelo de requisitos e vincular o modelo para tarefas de desenvolvimento. Você pode fazer isso por meio da vinculação de itens de trabalho [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] aos elementos no modelo.

Você pode vincular qualquer elemento para itens de trabalho, mas os elementos mais úteis são da seguinte maneira:

- Comentários que descreve as regras de negócio ou qualidade dos requisitos de serviço. Para obter mais informações, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).

### <a name="link-model-to-tests"></a>Modelo de link para testes

Use o modelo de requisitos para orientar o design dos testes de aceitação. Crie esses testes simultaneamente com o trabalho de desenvolvimento.

Para saber mais sobre essa técnica, consulte [desenvolver testes de um modelo de](../modeling/develop-tests-from-a-model.md).

### <a name="estimate-remaining-work"></a>Estimar o trabalho restante

Um modelo de requisitos pode ajudar a estimar o tamanho total do projeto em relação ao tamanho de cada iteração. Avaliar o número e a complexidade dos casos de uso e classes pode ajudá-lo a estimar o trabalho de desenvolvimento que serão necessário. Quando você concluiu a primeira algumas iterações, uma comparação dos requisitos coberto e ainda os requisitos para cobrir pode fornecer uma medida aproximada do custo e o escopo do restante do projeto.

No final de cada iteração, examine a atribuição de requisitos para iterações futuras. Ele pode ser útil representar o estado de software no final de cada iteração como um subsistema de um diagrama de caso de uso. A conversa, você pode mover os casos de uso e usar extensões de caso de um esses subsistemas para outro.

## <a name="levels-of-abstraction"></a>Níveis de abstração

Os modelos têm um intervalo de abstração em relação ao software. Os modelos mais concretos representam diretamente o código do programa e os modelos mais abstratos representam conceitos de negócios que podem ou não podem ser representados no código.

Um modelo pode ser exibido através de vários tipos de diagramas. Para obter informações sobre modelos e diagramas, consulte [criar modelos para o aplicativo](../modeling/create-models-for-your-app.md).

Tipos diferentes de diagrama são úteis para descrever o design em diferentes níveis de abstração. Muitos dos tipos de diagrama são úteis em mais de um nível. Esta tabela mostra como cada tipo de diagrama pode ser usado.

|Nível de design|Tipos de diagrama|
|------------------|-------------------|
|Processo de negócios<br /><br /> Noções básicas sobre o contexto no qual o sistema será usado o ajuda a entender o que os usuários que precisam dela.|-Diagramas de classe conceitual descrevem os conceitos de negócios usados dentro do processo de negócios.|
|Requisitos de usuário<br /><br /> Definição de que os usuários precisam do seu sistema.|-Regras de negócio e a qualidade dos requisitos de serviço podem ser descritos em documentos separados.|
|Design de nível alto<br /><br /> A estrutura geral do sistema: os principais componentes e como eles acoplar juntos.|-Diagramas dependência descrevem como o sistema está estruturado em partes interdependentes. Você pode validar o código de programa em diagramas de dependência para garantir que está sujeito à arquitetura.|
|Análise de código<br /><br /> Diagramas podem ser gerados no código.|-Diagramas de dependência mostram as dependências entre classes. Código atualizado pode ser validado em relação um diagrama de dependência.<br />-Diagramas de classe mostram as classes no código.|

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Vídeos**|![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [vídeos MSDN How Do I: como criar e usar modelos e diagramas UML (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML no Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [série MSDN How Do I: extensibilidade (Visual Studio 2010 Ultimate) e ferramentas de UML](http://go.microsoft.com/fwlink/?LinkID=214467)|
|**Fóruns**|- [Visualização do Visual Studio e ferramentas de modelagem](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Visualização do Visual Studio e modelagem SDK (ferramentas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Diários e artigos técnicos**|[Centro de arquitetura do MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Diretrizes de ferramentas de arquitetura do Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>Consulte também

[Usar modelos de desenvolvimento ágil](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) 
[criar modelos para o aplicativo](../modeling/create-models-for-your-app.md) 
[requisitos de usuário de modelo](../modeling/model-user-requirements.md) 
[modelo do aplicativo arquitetura](../modeling/model-your-app-s-architecture.md) 
[desenvolver testes de um modelo de](../modeling/develop-tests-from-a-model.md) 
[estruturar a solução de modelagem](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
