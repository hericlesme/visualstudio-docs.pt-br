---
title: "Sobre linguagens específicas do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: "26"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7bdd5f6f9561e3479d173a1e182ffa07649bc776
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="about-domain-specific-languages"></a>Sobre linguagens específicas do domínio
Ao contrário de uma linguagem de finalidade geral, como c# ou UML, uma linguagem específica de domínio (DSL) foi projetada para express instruções em um determinado problema de espaço ou domínio.  
  
 DSLs Well-Known incluem expressões regulares e SQL. Cada DSL é muito melhor do que uma linguagem de finalidade geral para descrever as operações em cadeias de caracteres de texto ou um banco de dados, mas pior para descrever as ideias que estão fora de seu próprio escopo. Setores individuais também têm seus próprios DSLs. Por exemplo, no setor de telecomunicações, chame descrição idiomas são amplamente usados para especificar a sequência dos estados em uma chamada telefônica e no ar de viagem setor padrão que DSL é usado para descrever as reservas de voo.  
  
 Sua empresa e seu projeto também lidam com conjuntos especiais de conceitos que podem ser descritos com uma DSL. Por exemplo, você pode definir uma DSL para um desses aplicativos:  
  
-   Plano de caminhos de navegação em um site da Web.  
  
-   Diagramas de fiação para componentes eletrônicos.  
  
-   Redes de belts transportadora e bagagem tratamento equipamento para um aeroporto.  
  
 Quando você cria uma DSL, você define uma *classe de domínio* para cada um dos conceitos importantes no domínio, como uma página da Web, lâmpada ou aeroporto check-in do suporte técnico. Definir *relações domínio* como hiperlink, durante a transmissão ou uma faixa de transportadora para vincular os conceitos.  
  
 Criarem usuários de seu DSL *modelos.* Os modelos são *instâncias* de DSL. Por exemplo, elas descrevem um site específico ou a fiação de um determinado dispositivo ou a sistema em um aeroporto específico de tratamento de bagagem.  
  
 Os usuários podem exibir um modelo como um diagrama ou um formulário do Windows. Modelos também podem ser exibidos como XML, que é como eles são armazenados. Ao definir uma DSL, você define como as instâncias de cada classe de domínio e as relações são exibidos na tela do usuário. Uma DSL típica é exibida como uma coleção de ícones ou retângulos conectados por setas.  
  
 A figura a seguir mostra um modelo pequeno em uma DSL diagramática:  
  
 ![Modelo de árvore da família Tudor](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>O que você pode fazer com DSLs  
 Um aplicativo típico de um DSL é gerar o código do programa ou outros artefatos. Quando você define sua DSL, você pode definir *modelos de texto* que ler um modelo de DSL e gerar arquivos de texto.  
  
 Por exemplo, você poderia escrever modelos que usam um plano de aeroporto e geram parte do software para bagagem tratamento, bem como alguns dos documentos do usuário que descrevem o plano.  
  
 Quando você tiver definido uma DSL, você pode distribuí-lo a outros usuários podem instalá-lo em seus próprios computadores. Os usuários de seu DSL podem criar e editar modelos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Você também pode definir os comandos de menu e outras ferramentas que ajudam os usuários editar DSL, restrições de validação para ajudar a garantir que o DSL está sendo usado corretamente e modelos de item que ajudam os usuários a criarem novas instâncias. Você pode encapsular um ou mais DSLs com suas ferramentas e outros [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões como um pacote integrado.  
  
 Normalmente, uma linguagem específica de domínio é criada quando uma equipe de desenvolvimento precisa gravar um código semelhante para vários produtos. Por exemplo, uma empresa especializada em bagagem tratamento sistemas pode definir uma DSL de acompanhar bagagem do qual podem gerar alguns dos códigos de cada instalação. Os benefícios de DSL é que ele pode ser compreendido por seus clientes, que o código gerado dele é confiável e que o sistema pode ser atualizado rapidamente se alterarem às necessidades dos clientes.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]permite criar uma linguagem específica de domínio que tem seu próprio designer gráfico e a notação de seu próprio diagrama e, em seguida, usar a linguagem para gerar código-fonte apropriado para cada projeto.  
  
## <a name="domain-specific-development"></a>Desenvolvimento de domínio específico  
 Desenvolvimento específico de domínio é o processo de identificar as partes de seus aplicativos que podem ser modelados usando uma linguagem específica de domínio e, em seguida, construindo o idioma e implantá-lo para os desenvolvedores de aplicativos. Os desenvolvedores usam a linguagem específica de domínio para criar modelos que são específicos para seus aplicativos, use os modelos para gerar código-fonte e, em seguida, use o código-fonte para desenvolver os aplicativos.  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>Aspectos do desenvolvimento de gráfico específica de domínio  
 Uma linguagem específica de domínio gráfica deve incluir os seguintes recursos:  
  
-   Notation  
  
-   Modelo de domínio  
  
-   Geração de artefato  
  
-   Serialização  
  
-   Integração com o Visual Studio  
  
### <a name="notation"></a>Notation  
 Uma linguagem específica de domínio deve ter um conjunto relativamente pequeno de elementos que podem ser facilmente definidas e estendidos para representar construções específicas do domínio. Uma notação consiste em formas, que representam os elementos, e conectores, que representam as relações entre os elementos na superfície de um diagrama gráfico. Em [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], as formas podem ser estendidas e refinadas para representar os elementos da sua linguagem específica de domínio.  
  
### <a name="domain-model"></a>Modelo de domínio  
 Uma linguagem específica de domínio deve combinar o conjunto de elementos e as relações entre eles em uma gramática coerente. Ele também deve definir se combinações de elementos e relações são válidas. Por exemplo, linguagens de programação normalmente evitar herança circular, em que uma classe é derivada de uma classe de segundo e a segunda classe é derivada da classe primeiro. Restrições também podem ser usadas para expressar a lógica de negócios, por exemplo, uma pessoa não pode ser um dependente de si próprio. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]usa as restrições para expressar os tipos de restrições que exigem mais idiomas de domínio específico.  
  
### <a name="artifact-generation"></a>Geração de artefato  
 Um dos principais motivos de uma linguagem específica de domínio é gerar um artefato, por exemplo, o código-fonte, um arquivo XML ou outros dados utilizáveis. Normalmente, uma alteração no modelo significa que uma alteração no artefato. Você pode usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para gerar os artefatos e gerá-los novamente quando você alterar o modelo.  
  
### <a name="serialization"></a>Serialização  
 Uma linguagem específica de domínio deve ser persistida em alguma forma que pode ser editada, salvo, fechada e recarregada. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]usa um formato XML que lhe permite definir e personalizar como sua linguagem específica de domínio é serializada ou persistente.  
  
### <a name="integration-with-visual-studio"></a>Integração com o Visual Studio  
 Porque [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] está hospedado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ele estende muitas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janelas e controles. Ele também permite personalizar o comportamento dos comandos de menu, itens de caixa de ferramentas e outros elementos da interface do usuário.  
  
 Você também pode criar um adaptador de barramento de modelo para sua linguagem específica de domínio. Este adaptador permite que um modelo de referência e elementos dentro de um modelo e permite que você escreva o código que pode acessar e atualizar uma instância de DSL. Usando o mecanismo eficiente de barramento de modelo, você pode escrever [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões que funcionam com vários modelos. Você também pode escrever aplicativos independentes que trabalham com modelos. Para obter mais informações, consulte [integrar modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Benefícios de desenvolvimento específicas do domínio  
 Uma linguagem específica de domínio pode fornecer os seguintes benefícios:  
  
-   Contém construções que se ajuste exatamente o problema de espaço.  
  
     Ao contrário de linguagens de finalidade geral, uma linguagem específica de domínio consiste em elementos e relações que representam diretamente a lógica do problema de espaço. Por exemplo, um aplicativo de apólices deve incluir elementos de políticas e declarações. Uma linguagem específica de domínio torna mais fácil de criar o aplicativo e localizar e corrigir erros de lógica.  
  
-   Permite que desenvolvedores não e as pessoas que não conhecem o domínio entender o design geral.  
  
     Usando uma linguagem específica de domínio gráfica, você pode criar uma representação visual do domínio para que os desenvolvedores não podem compreender facilmente o design do aplicativo.  
  
-   Torna mais fácil de criar um protótipo do aplicativo final.  
  
     Os desenvolvedores podem usar o código que gera o modelo para criar um aplicativo de protótipo que eles podem mostrar aos clientes.  
  
## <a name="the-process-of-domain-specific-development"></a>O processo de desenvolvimento específicas do domínio  
 A maioria das equipes de desenvolvimento de software que usam linguagens específicas de domínio siga estas etapas para criar e usar seus modelos:  
  
-   A equipe distingue as partes de variável do domínio partes nunca ser alterado.  
  
-   Os desenvolvedores de escrever código para as partes fixas e deixam os pontos de extensão para as partes de variável.  
  
-   O gerente de desenvolvimento de software ou o arquiteto cria uma linguagem específica de domínio que incorpora os padrões de design das partes fixas do domínio e os pontos de extensão para as partes de variável.  
  
-   O gerente de desenvolvimento de software ou o arquiteto implanta a linguagem específica de domínio para os desenvolvedores de vários aplicativos que produz a equipe.  
  
-   Cada desenvolvedor cria um modelo que se aplica ao aplicativo específico.