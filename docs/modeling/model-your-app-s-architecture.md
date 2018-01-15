---
title: Modelo de aplicativo &#39; arquitetura de s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ce471f2229744c9ee72f16a3b784f9e09823375d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="model-your-app39s-architecture"></a>Modelo de aplicativo &#39; arquitetura
Para ajudar a garantir que seu sistema de software ou aplicativo atende aos seus usuários necessidades, você pode criar modelos no Visual Studio como parte de sua descrição da estrutura geral e o comportamento do seu aplicativo ou sistema de software. Usando modelos, você também pode descrever padrões que são usados em todo o projeto. Esses modelos de ajudarão-lo a entender a arquitetura existente, discuta as alterações e comunicar sua intenção claramente.  
  
 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 A finalidade de um modelo é para reduzir as ambiguidades que ocorrem nas descrições de idioma natural e para ajudar você e seus colegas para visualizar o design e discutir projetos alternativos. Um modelo deve ser usado junto com outros documentos ou discussões. Por si só, um modelo não representa uma especificação completa da arquitetura.  
  
> [!NOTE]
>  Ao longo deste tópico, "sistema" significa que o software que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de hardware e software, ou um único aplicativo ou uma parte de um aplicativo.  
  
 A arquitetura de um sistema pode ser dividida em duas áreas:  
  
-   [Design de alto nível](#Structure). Descreve os principais componentes e como eles interagem entre si para atender a cada requisito. Se o sistema for grande, cada componente pode ter seu próprio design de alto nível que mostra como é composto de componentes menores.  
  
-   [Padrões de design](#Patterns) e convenções usadas em todo os designs de componentes. Um padrão descreve uma abordagem específica para atingir uma meta de programação. Usando os mesmos padrões durante um projeto, sua equipe pode reduzir o custo de fazer alterações e desenvolvimento de novo software.  
  
##  <a name="Structure"></a>Design de alto nível  
 Um design de alto nível descreve os principais componentes do seu sistema e como eles interagem entre si para atingir as metas do design. As atividades na lista a seguir são envolvidas no desenvolvimento de design de alto nível, embora não necessariamente de uma determinada sequência.  
  
 Se você estiver atualizando o código existente, você pode começar descrevendo os principais componentes. Certifique-se de compreender as alterações para os requisitos de usuário e adicionar ou modificar as interações entre os componentes. Se você estiver desenvolvendo um novo sistema, começar com noções básicas sobre os principais recursos de necessidades dos usuários. Você pode, em seguida, explore sequências de interações para os casos de uso principal e, em seguida, consolidar as sequências em um projeto de componente.  
  
 Em cada caso, ele é útil para desenvolver as diferentes atividades em paralelo e desenvolva o código e testa mais cedo. Evite tentar concluir um dos seguintes aspectos antes de começar outra. Normalmente, os requisitos e seu conhecimento sobre a melhor maneira de criar o sistema serão alterado enquanto você estiver escrevendo e o código de teste. Portanto, você deve começar a compreensão e os principais recursos do seu design e os requisitos de codificação. Preencha os detalhes nas últimas iterações do projeto.  
  
-   [Noções básicas sobre os requisitos de](#Requirements). O ponto de partida de qualquer design é uma compreensão clara de necessidades dos usuários.  
  
-   [Padrões de arquitetura](#BigDecisions). As escolhas feitas sobre as principais tecnologias e elementos de arquitetura do sistema.  
  
-   Modelo de dados dos componentes e Interfaces. Você pode desenhar diagramas de classe para descrever as informações que são transmitidas entre componentes e armazenadas dentro dos componentes.  
  
##  <a name="Requirements"></a>Noções básicas sobre os requisitos  
 O design de alto nível de um aplicativo completo com mais eficácia é desenvolvido junto com um modelo de requisitos ou outra descrição das necessidades dos usuários. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
 Se o sistema que você está desenvolvendo um componente em um sistema maior, parte ou todas as suas necessidades podem ser incorporadas em interfaces programáticas.  
  
 O modelo de requisitos fornece essas partes essenciais de informações:  
  
-   Interfaces de fornecido. Uma interface fornecida lista os serviços ou as operações do sistema ou o componente deve fornecer a seus usuários, independentemente de estarem usuários humanos ou outros componentes de software.  
  
-   Interfaces necessárias. Uma interface necessária lista os serviços ou as operações do sistema ou o componente pode usar. Em alguns casos, você poderá criar todos esses serviços como parte do seu próprio sistema. Em outros casos, especialmente se você estiver criando um componente que pode ser combinado com outros componentes em muitas configurações, a interface necessária será definida por considerações externas.  
  
-   Qualidade de serviço. O desempenho, segurança, robustez e outros objetivos e restrições que o sistema deve atender.  
  
 O modelo de requisitos é gravado do ponto de vista de usuários do seu sistema, se eles são pessoas ou outros componentes de software. Eles sabem nada sobre o funcionamento do seu sistema. Por outro lado, sua meta em um modelo de arquitetura é descrever as operações internas e mostrar como elas cumprem os usuários precisa.  
  
 Manter os requisitos e modelos de arquitetura separados é útil porque ela torna mais fácil discutir os requisitos com os usuários. Ele também ajuda refatorar o design e considere arquiteturas alternativas, manter os requisitos inalterada.  
  
 A quantidade de detalhes que devem ser colocados em um requisitos ou um modelo de arquitetura depende a escala do projeto e o tamanho e a distribuição da equipe. Uma equipe pequena em um projeto de curto pode ir não mais do que fazer um rascunho de um diagrama de classe de conceitos de negócios e alguns padrões de design; um projeto grande distribuído em mais de uma região precisaria significativamente mais detalhes.  
  
##  <a name="BigDecisions"></a>Padrões de arquitetura  
 No início do desenvolvimento de um, você precisa escolher as principais tecnologias e os elementos dos quais depende o design. As áreas em que essas opções devem ser feitas incluem o seguinte:  
  
-   Base de opções de tecnologia, como a escolha entre um banco de dados e um sistema de arquivos e a escolha entre um aplicativo de rede e um cliente Web e assim por diante.  
  
-   Opções de estruturas, como a opção de Windows Workflow Foundation ou o ADO.NET Entity Framework.  
  
-   Opções de método de integração, por exemplo, entre um barramento de serviço corporativo ou de um canal de ponto a ponto.  
  
 Essas opções frequentemente são determinadas pela qualidade dos requisitos de serviço, como a escala e a flexibilidade e podem ser feitas antes que os requisitos detalhados são conhecidos. Em um sistema grande, a configuração de hardware e software são altamente inter-relacionadas.  
  
 As seleções feitas afetam como usar e interpretar o modelo de arquitetura. Por exemplo, em um sistema que usa um banco de dados, associações em um diagrama de classe podem representar relações ou chaves estrangeiras no banco de dados, enquanto um sistema baseado em arquivos XML, as associações podem indicar referências cruzadas que usam XPath. Em um sistema distribuído, mensagens em um diagrama de sequência podem representar mensagens em uma transmissão; em um aplicativo independente, podem representar chamadas de função.  
  
##  <a name="Patterns"></a>Padrões de design  
 Um padrão de design é um resumo de como criar um aspecto específico do software, especialmente aquelas que se repete em diferentes partes do sistema. Adotando uma abordagem uniforme entre o projeto, reduzir o custo de design, garantir a consistência na interface do usuário e reduzir o custo de entender e alterar o código.  
  
 Alguns padrões de design geral como observador são bem conhecidos e amplamente aplicável. Além disso, há padrões que são aplicáveis apenas ao seu projeto. Por exemplo, em um sistema de vendas da Web, haverá diversas operações no código onde as alterações são feitas para o pedido do cliente. Para garantir que o estado do pedido é exibido corretamente em cada estágio, todas essas operações devem seguir um protocolo específico para atualizar o banco de dados.  
  
 É parte do trabalho de arquitetura de software determinar qual padrões devem ser adotada em design. Isso geralmente é uma tarefa em andamento, porque novos padrões e aprimoramentos para os padrões existentes serão descobertos conforme o andamento do projeto. É útil organizar o plano de desenvolvimento para que você utilizar cada um dos seus padrões de design principais mais cedo.  
  
 A maioria dos padrões de design podem ser incorporados parcialmente em código do framework. Parte do padrão pode ser reduzido para exigir que o desenvolvedor usar classes específicos ou componentes, como uma camada de acesso de banco de dados que garante que o banco de dados é tratado corretamente.  
  
 Um padrão de design é descrito em um documento e normalmente inclui estas partes:  
  
-   Nome.  
  
-   Descrição do contexto no qual ele é aplicável. O critério deve fazer com que um desenvolvedor aplicar esse padrão?  
  
-   Breve explicação do problema que será resolvido.  
  
-   Modelo de partes principais e suas relações. Eles podem ser classes ou componentes e interfaces com associações e dependências entre eles. Os elementos geralmente se encaixam em duas categorias:  
  
-   Convenções de nomenclatura.  
  
-   Descrição de como o padrão resolve o problema.  
  
-   Descrição de variações de que os desenvolvedores poderá adotar.  
  
## <a name="see-also"></a>Consulte também  
 [Visualizar código](../modeling/visualize-code.md)   
 [Requisitos do modelo de usuário](../modeling/model-user-requirements.md)   
 [Desenvolver testes de um modelo](../modeling/develop-tests-from-a-model.md)   
 [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)