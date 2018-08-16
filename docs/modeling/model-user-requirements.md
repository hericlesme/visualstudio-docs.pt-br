---
title: Requisitos de usuário do modelo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a8f79e80b5b4e4e14772548ad92e8886150749b7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749051"
---
# <a name="model-user-requirements"></a>Requisitos de usuário do modelo

Visual Studio o ajuda a entender, discuta e se comunicar suas necessidades de usuários ao desenhar diagramas sobre suas atividades e a parte um sistema desempenha no ajudando a atingir suas metas. Um modelo de requisitos é um conjunto desses diagramas, cada um deles se concentra em um aspecto das necessidades dos usuários. Para uma demonstração de vídeo, consulte: [modelagem de domínio da empresa](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).

 Para ver quais versões do Visual Studio oferecem suporte a cada tipo de modelo, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Um modelo de requisitos ajuda a:

-   Se concentrar em comportamento externos do sistema, separadamente do seu design interno.

-   Descreva os usuários e stakeholders precisa com muito menos ambiguidade que no idioma natural.

-   Defina um consistente Glossário de termos que podem ser usados por usuários, desenvolvedores e testadores.

-   Reduza lacunas e inconsistências nos requisitos.

-   Reduza o trabalho necessário para responder às alterações de requisitos.

-   Planeje a ordem na qual os recursos serão desenvolvidos.

-   Use os modelos como uma base para testes de sistema, fazendo uma relação clara entre os testes e os requisitos. Quando os requisitos de alterarem, essa relação ajuda a atualizar os testes corretamente. Isso garante que o sistema atende aos requisitos de novo.

 Um modelo de requisitos fornece o maior benefício de se você usá-lo para discussões de foco com os usuários ou seus representantes e revisá-lo no início de cada iteração. Você não precisa ser concluída em detalhes antes de escrever código. Um aplicativo de trabalho parcialmente, mesmo se muito simplificado, geralmente constitui a base mais interessantes para discussão de requisitos com usuários. O modelo é uma maneira eficiente de resumir os resultados dessas conversas. Para obter mais informações, consulte [usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Durante esses tópicos, "sistema" significa que o sistema ou o aplicativo que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de hardware e software; ou um único aplicativo; ou um componente de software dentro de um sistema maior. Em cada caso, o modelo de requisitos descreve o comportamento que é visível fora de seu sistema, através de uma interface de usuário ou a API.

## <a name="common-tasks"></a>Tarefas comuns

Você pode criar várias exibições diferentes dos requisitos dos usuários.  Cada modo de exibição fornece um tipo específico de informações.  Quando você cria esses modos de exibição, é melhor mudam frequentemente uns aos outros. Você pode iniciar a partir de qualquer modo de exibição.

|Diagrama ou documento|Ele descreve em um modelo de requisitos|Seção|
|-------------------------|-----------------------------------------------|-------------|
|Diagrama conceitual de classe|Glossário de tipos que são usados para descrever os requisitos. os tipos visíveis na interface do sistema.||
|Outros documentos ou itens de trabalho|Critérios de desempenho, segurança, facilidade de uso e a confiabilidade.|[Que descreve a qualidade dos requisitos de serviço](#QoSRequirements)|
|Outros documentos ou itens de trabalho|Restrições e regras não específicas a um determinado caso de uso|[Mostrando as regras de negócio](#BusinessRules)|

 Observe que a maioria dos tipos de diagrama pode ser usada para outras finalidades. Para obter uma visão geral dos tipos de diagrama, consulte [criar modelos para o aplicativo](../modeling/create-models-for-your-app.md).

##  <a name="BusinessRules"></a> Mostrando as regras de negócio

Uma regra de negócios é um requisito que não está associado um caso de uso específico e deve ser observado em todo o sistema.

 Muitas regras de negócio são restrições nas relações entre as classes conceituais. Você pode escrever esses *estático * * as regras de negócio* como comentários associados as classes relevantes em um diagrama conceitual de classe. Por exemplo:

 ![Regra em comentário anexado à classe Order.](../modeling/media/uml_reqmcd2.png)

 *Regras de negócio dinâmico* restringir as sequências permitidas de eventos. Por exemplo, você deve usar um diagrama de sequência ou uma atividade para mostrar que um usuário deve fazer logon antes de executar outras operações no sistema.

 No entanto, muitas regras dinâmicas podem ser mais eficaz e genericamente declaradas substituindo-os por regras estáticas. Por exemplo, você pode adicionar um atributo booleano 'Registrado no' a uma classe no modelo conceitual de classe. Você seria adicionar conectado como pós-condição do log em caso de uso e adicioná-lo como uma pré-condição da maioria dos casos de uso. Essa abordagem permite que você evite definir todas as combinações possíveis de sequências de eventos. Também é mais flexível quando você precisa adicionar novos casos de uso para o modelo.

 Observe que a opção aqui é sobre como definir os requisitos e que isso acontece independentemente de como implementar os requisitos no código de programa.

 Os tópicos a seguir fornecem mais informações:

|Para saber mais sobre|Ler|
|--------------------|----------|
|Como desenvolver o código que segue as regras de negócio|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

##  <a name="QoSRequirements"></a> Que descreve a qualidade dos requisitos de serviço

Há várias categorias de qualidade de requisito de serviço. Elas incluem o seguinte:

-   Desempenho

-   Segurança

-   Usabilidade

-   Confiabilidade

-   Robustez

Você pode incluir alguns desses requisitos nas descrições de casos de uso específico. Outros requisitos não são específicos para casos de uso e com mais eficácia são gravados em um documento separado. Quando possível, é útil cumprir o vocabulário definido pelo modelo de requisitos. No exemplo a seguir, observe que as palavras principais usadas requisitos de títulos de atores, casos de uso e classes nas ilustrações anteriores:

Se um restaurante exclui um Item de Menu enquanto uma refeição ordenação de um cliente, qualquer Item do pedido que se refere a esse Item de Menu será exibido em vermelho.

Consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md) para aprender a desenvolver o código que segue a qualidade dos requisitos de serviço.

## <a name="see-also"></a>Consulte também

- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
- [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)
