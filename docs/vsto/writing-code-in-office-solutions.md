---
title: Escrevendo código em soluções do Office | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6119db86fdd67079b63434a6bb494cb04cd31d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="writing-code-in-office-solutions"></a>Escrevendo código em soluções do Office
  Há alguns aspectos de escrever código em projetos do Office que são diferentes de outros tipos de projetos no Visual Studio. Muitas dessas diferenças estão relacionadas à forma como os modelos de objeto do Office são expostos para código gerenciado. Outras diferenças estão relacionadas ao design de projetos do Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>O código gerenciado e programação do Office  
 A tecnologia de chave que torna possível a criação de uma solução integrada do Microsoft Office é automação, que é parte da tecnologia de modelo de objeto de componente (COM). A automação permite que você pode usar código para criar e controlar os objetos de software expostos por qualquer aplicativo, DLL, ou controle ActiveX que oferece suporte as interfaces programáticas apropriadas.  
  
### <a name="understanding-primary-interop-assemblies"></a>Noções básicas sobre Assemblies de interoperabilidade primários  
 Aplicativos do Microsoft Office expõem grande parte da sua funcionalidade à automação. No entanto, você não pode usar código gerenciado (como Visual Basic ou c#) diretamente para automatizar aplicativos do Office. Para automatizar aplicativos do Office usando código gerenciado, você deve usar a assemblies de interoperabilidade primários (PIAs) do Office. Os assemblies de interoperabilidade primários permitem que o código gerenciado interagir com o modelo de objeto COM base em aplicativos do Office.  
  
 Todos os aplicativos do Microsoft Office têm um PIA. Quando você cria um projeto do Office no Visual Studio, uma referência para o PIA apropriado é automaticamente adicionada ao projeto. Para automatizar os recursos de outros aplicativos do Office do projeto, você deve adicionar manualmente uma referência para o PIA apropriado. Para obter mais informações, consulte [como: destino Office aplicativos por meio de Assemblies de interoperabilidade primários](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="using-primary-interop-assemblies-at-design-time-and-run-time"></a>Usando Assemblies de interoperabilidade primários no tempo de Design e tempo de execução  
 Você deve ter os PIAs do Office instalado e registrado no cache de assembly global em seu computador de desenvolvimento para executar a maioria das tarefas de desenvolvimento. Para obter mais informações, consulte [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 PIAs do Office não são necessário em computadores de usuários finais para executar soluções do Office destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. Para obter mais informações, consulte [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="using-types-in-primary-interop-assemblies"></a>Usando tipos em Assemblies de interoperabilidade primários  
 PIAs do Office contêm uma combinação de tipos que expõem o modelo de objeto dos aplicativos do Office e infraestrutura adicional que não se destina a ser usado diretamente no seu código. Para obter uma visão geral dos tipos PIAs do Office, consulte [visão geral de Classes e Interfaces de Assemblies de interoperabilidade primários do Office](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5).  
  
 Como os tipos de PIAs do Office correspondem aos tipos de modelos de objeto baseado em COM, a maneira como você usa esses tipos geralmente é diferente de outros tipos gerenciados. Por exemplo, a maneira como você chamar métodos que têm parâmetros opcionais em um assembly de interoperabilidade primária do Office depende de linguagem de programação que você está usando em seu projeto. Para mais informações, consulte os seguintes tópicos:  
  
-   [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="programming-model-of-office-projects"></a>Modelo de programação de projetos do Office  
 Todos os projetos do Office incluem uma ou mais classes geradas que fornecem o ponto de entrada para seu código. Essas classes também fornecem acesso ao modelo de objeto do aplicativo host e acesso a recursos, como painéis de ações e painéis de tarefas personalizados.  
  
### <a name="understanding-the-generated-classes"></a>Noções básicas sobre Classes geradas  
 Em projetos de nível de documento para Excel e Word, a classe gerada é semelhante a um objeto de nível superior no modelo de objeto do aplicativo. Por exemplo, gerado `ThisDocument` classe em um projeto de documento do Word fornece os mesmos membros como o <xref:Microsoft.Office.Interop.Word.Document> classe no modelo de objeto do Word. Para obter mais informações sobre as classes geradas no nível de documento, consulte [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
 Projetos de suplemento do VSTO fornecem uma classe gerada chamada `ThisAddIn`. Essa classe não se assemelha a uma classe no modelo de objeto do aplicativo host. Em vez disso, essa classe representa o Add-in do VSTO em si, e fornece membros, que você pode usar para acessar o modelo de objeto do aplicativo host e acessar outros recursos disponíveis para suplementos do VSTO. Para obter mais informações, consulte [Programando a validação](../vsto/programming-vsto-add-ins.md).  
  
 Todas as classes geradas em projetos do Office incluem `Startup` e `Shutdown` manipuladores de eventos. Para começar a escrever código, você normalmente adiciona código para esses manipuladores de eventos. Para inicializar o suplemento do VSTO, você pode adicionar código para o `Startup` manipulador de eventos. Para limpar os recursos usados pelo seu suplemento do VSTO, você pode adicionar código para o `Shutdown` manipulador de eventos. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-generated-classes-at-run-time"></a>Acessar as Classes geradas em tempo de execução  
 Quando uma solução do Office é carregada, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria uma instância de cada uma das classes geradas em seu projeto. Você pode acessar esses objetos de qualquer código no seu projeto usando o `Globals` classe. Por exemplo, você pode usar o `Globals` classe para chamar o código no `ThisAddIn` classe de um manipulador de eventos de um botão de faixa de opções em um suplemento do VSTO.  
  
 Para obter mais informações, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Considerações sobre o Namespace em soluções do Office  
 Não é possível alterar o *namespace padrão* (ou *namespace raiz* no Visual Basic) de um projeto do Office depois de criar o projeto. O namespace padrão corresponderá sempre o nome do projeto que você especificou quando criou o projeto. Se você renomear o projeto, o namespace padrão não é alterado. Para obter mais informações sobre o namespace padrão em projetos, consulte [página de aplicativo, Designer de projeto &#40;C&#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) e [página de aplicativo, Designer de projeto &#40;Visual Basic&#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="changing-the-namespace-of-host-item-classes-in-c-projects"></a>Alterar o Namespace das Classes de Item de Host em projetos c#  
 Classes de item de host (por exemplo, o `ThisAddIn`, `ThisWorkbook`, ou `ThisDocument` classes) têm seus próprios namespaces em projetos do Visual c# Office. Por padrão, o namespace para itens de host em seu projeto coincide com o nome do projeto que você especificou quando criou o projeto.  
  
 Para alterar o namespace dos itens de host em um projeto do Visual c# Office, use o **Namespace para Item de Host** propriedade. Para obter mais informações, consulte [propriedades em projetos do Office](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Linguagens de programação com suporte em projetos do Office  
 Os modelos de projeto do Office no Visual Studio oferecem suporte a somente os idiomas programação Visual Basic e Visual c#. Portanto, esses modelos de projeto estão disponíveis apenas no **Visual Basic** e **Visual C#** nós do **novo projeto** da caixa de diálogo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Opção de idioma e a programação do Office  
 Microsoft Office e do Visual Basic for Applications (VBA) foram desenvolvidos para trabalhar juntos para otimizar o fluxo de trabalho de personalização do aplicativo. Visual Basic tem herdada alguns desses desenvolvimentos. Por exemplo, Visual Basic oferece suporte a parâmetros opcionais, que significa que você pode escrever menos código ao chamar alguns métodos em assemblies de interoperabilidade primários do Microsoft Office que quando você usa o Visual c#.  
  
## <a name="programming-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programação com o Visual Basic vs. Visual c# em soluções do Office  
 Você pode criar soluções do Office usando o Visual Basic ou Visual c#. Como os modelos de objeto do Microsoft Office foram projetados para ser usado com o Microsoft Visual Basic for Applications (VBA), os desenvolvedores do Visual Basic podem trabalhar confortavelmente com os objetos expostos pelos aplicativos do Microsoft Office. Visual c# os desenvolvedores podem usar a maioria dos mesmos recursos como os desenvolvedores do Visual Basic, mas há alguns casos em que for necessário gravar código adicional para usar os modelos de objeto do Office. Também há algumas diferenças entre os recursos de programação básicos no desenvolvimento do Office e código gerenciado escrito em Visual Basic e c#.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Principais diferenças entre o Visual Basic e Visual c#  
 A tabela a seguir mostra as principais diferenças entre o Visual Basic e Visual c# no desenvolvimento do Office.  
  
|Recurso|Descrição|Suporte ao Visual Basic|Suporte do Visual c#|  
|-------------|-----------------|--------------------------|------------------------|  
|Parâmetros opcionais|Muitos métodos do Microsoft Office têm parâmetros que não são necessários quando você chamar o método. Se nenhum valor é passado para o parâmetro, um valor padrão será usado.|Visual Basic oferece suporte a parâmetros opcionais.|Visual c# oferece suporte a parâmetros opcionais na maioria dos casos. Para obter mais informações, consulte [parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Passando parâmetros por referência|Parâmetros opcionais na maioria dos assemblies de interoperabilidade primários do Microsoft Office podem ser passados por valor. No entanto, em alguns assemblies de interoperabilidade primários, os parâmetros opcionais que aceitam os tipos de referência devem ser transmitidos por referência.<br /><br /> Para obter mais informações sobre parâmetros de tipo de valor e referência, consulte [passando argumentos por valor e por referência &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (para Visual Basic) e [passando parâmetros &#40;C&#35; Guia de programação&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Nenhum trabalho adicional é necessário para passar parâmetros por referência. O compilador do Visual Basic passa automaticamente os parâmetros por referência quando necessário.|Na maioria dos casos, o compilador do Visual c# automaticamente passa os parâmetros por referência quando necessário. Para obter mais informações, consulte [parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Propriedades com parâmetros|Algumas propriedades aceitam parâmetros e atuam como funções de somente leitura.|Visual Basic oferece suporte às propriedades que aceitam parâmetros.|Visual c# oferece suporte às propriedades que aceitam parâmetros.|  
|Associação tardia|Associação tardia consiste em determinar as propriedades de objetos em tempo de execução, em vez de variáveis de conversão para o tipo de objeto em tempo de design.|Visual Basic executa a associação tardia quando **Option Strict** está desativado. Quando **Option Strict** está ativada, você deverá converter explicitamente objetos e tipos de uso no <xref:System.Reflection> namespace para acessar membros de associação tardia. Para obter mais informações, consulte [associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md).|Visual c# executa a associação tardia em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Para obter mais informações, consulte [associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Principais diferenças entre o desenvolvimento do Office e o código gerenciado  
 A tabela a seguir mostra as principais diferenças entre o desenvolvimento do Office e código gerenciado escrito em Visual Basic ou Visual c#.  
  
|Recurso|Descrição|Suporte do Visual Basic e Visual c#|  
|-------------|-----------------|-----------------------------------------|  
|Índices de matriz|O limite inferior de matriz de coleções de aplicativos do Microsoft Office começa com 1. Visual Basic e Visual c# usam matrizes de base 0. Para obter mais informações, consulte [matrizes &#40;C&#35; guia de programação&#41; ](/dotnet/csharp/programming-guide/arrays/index) e [matrizes no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Para acessar o primeiro item de uma coleção no modelo de objeto de um aplicativo do Microsoft Office, use o índice 1, em vez de 0.|  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Eventos em projetos do Office](../vsto/events-in-office-projects.md)   
 [Como: destinar aplicativos do Office por meio de Assemblies de interoperabilidade primários](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Como: criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)   
 [Desenvolvimento colaborativo de soluções do Office](../vsto/collaborative-development-of-office-solutions.md)  
  
  