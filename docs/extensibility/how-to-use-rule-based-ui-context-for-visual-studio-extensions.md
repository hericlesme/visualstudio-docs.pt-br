---
title: 'Como: usar o contexto de interface do usuário baseada em regras para extensões do Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8597c413c899b54e61e848649c3c524cbdb20724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Como: usar o contexto de interface do usuário baseada em regras para extensões do Visual Studio
O Visual Studio permite o carregamento de VSPackages quando determinados conhecidos <xref:Microsoft.VisualStudio.Shell.UIContext>s são ativados. No entanto, esses contextos de interface do usuário não são muito bem com o detalhamento, não deixando os autores de extensão nenhuma opção de mas para selecionar um contexto de interface do usuário disponíveis que ativa antes do ponto realmente desejasse VSPackage para carregar. Para obter uma lista de contextos de interface de usuário bem conhecidos, consulte <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Carregar os pacotes pode ter um impacto no desempenho e carregá-los antes que eles são necessários não é a prática recomendada. Visual Studio 2015 introduziu o conceito de baseada em regras contextos de interface do usuário, um mecanismo que permite que os autores de extensão definir as condições precisas sob a qual um contexto de interface do usuário é ativado e carregados VSPackages associados.  
  
## <a name="rule-based-ui-context"></a>Contexto de interface do usuário com base em regra  
 Uma regra de"" consiste em um novo contexto de interface do usuário (uma GUID) e uma expressão booleana que faz referência a um ou mais "termos" combinado com lógica "e", "ou", "não" operações. "Termos" são avaliados dinamicamente em tempo de execução e a expressão é avaliada novamente sempre que qualquer uma das suas alterações de termos. Quando a expressão é avaliada como true, o contexto de interface do usuário associado está ativado. Caso contrário, o contexto de interface do usuário é desativado.  
  
 Contexto de interface do usuário com base em regra pode ser usado em uma variedade de maneiras:  
  
1.  Especifica as restrições de visibilidade de comandos e janelas de ferramenta. Você pode ocultar as janelas de ferramentas/comandos até que a regra de contexto de interface do usuário seja atendida.  
  
2.  Restrições de carga como automático: pacotes de carregamento automático apenas quando a regra é atendida  
  
3.  Tarefa atrasada: atrasar o carregamento até que um intervalo especificado tiver passado e a regra ainda é atingida.  
  
 O mecanismo pode ser usado por qualquer extensão do Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Criar um contexto de interface do usuário com base em regra  
 Suponha que você tenha uma extensão chamada TestPackage, que oferece um comando de menu que se aplica somente a arquivos com extensão ". config". Antes de VS2015, a melhor opção foi carregar TestPackage quando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> foi ativado com o contexto de interface do usuário. Isso não é eficiente, pois a solução carregada não pode conter até um arquivo. config. Informe-nos como contexto de interface do usuário com base em regras pode ser usado para ativar um contexto de interface do usuário somente quando um arquivo com extensão. config está selecionada e carregar TestPackage quando o contexto da interface do usuário é ativado.  
  
1.  Definir um novo GUID UIContext e adicionar à classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Por exemplo, vamos supor que um novo UIContext "UIContextGuid" é a ser adicionado. O GUID criado (você pode criar um GUID clicando em Ferramentas -> criar guid) é "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Você, em seguida, adicione o seguinte em sua classe de pacote:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Para os atributos, adicione o seguinte: (os detalhes desses atributos serão explicados posteriormente)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Esses metadados definem o novo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e uma expressão que faz referência a um único termo, "DotConfig". O termo "DotConfig" é avaliada como true, sempre que a seleção atual na hierarquia do active tem um nome que corresponde ao padrão de expressão regular "\\. config$" (termina com ". config"). O valor (padrão) define um nome opcional para a regra útil para depuração.  
  
     Os valores do atributo são adicionados ao pkgdef gerado durante o tempo de compilação posteriormente.  
  
2.  No arquivo VSCT para comandos do TestPackage, adicione o sinalizador "DynamicVisibility" para os comandos apropriados:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Na seção Visibilidades do VSCT, unir os comandos apropriados para o novo UIContext GUID definido em 1 #:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Na seção de símbolos, adicione a definição do UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Agora, os comandos de menu de contexto para arquivos de config ficará visíveis apenas quando o item selecionado no Gerenciador de soluções é um arquivo ". config" e o pacote não será carregado até que um desses comandos é selecionado.  
  
 Em seguida, vamos usar um depurador para confirmar que o pacote é carregado apenas quando é esperado. Para depurar TestPackage:  
  
1.  Definir um ponto de interrupção no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
2.  Compile o TestPackage e iniciar a depuração.  
  
3.  Criar um projeto ou abrir um.  
  
4.  Selecione qualquer arquivo com uma extensão diferente. config. O ponto de interrupção não deve ser atingido.  
  
5.  Selecione o arquivo App. config.  
  
 O TestPackage carrega e interrompida no ponto de interrupção.  
  
## <a name="adding-more-rules-for-ui-context"></a>Adicionar mais regras para o contexto de interface do usuário  
 Como as regras de contexto de interface do usuário são expressões Boolianas, você pode adicionar mais restrito de regras para um contexto de interface do usuário. Por exemplo, no contexto da interface de usuário acima, você pode especificar que a regra se aplica somente quando uma solução com um projeto é carregada. Dessa forma, os comandos serão exibidos se você abrir um arquivo ". config" como um arquivo autônomo, não como parte de um projeto.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Agora, a expressão referencia três termos. Os primeiros dois termos, "SingleProject" e "MultipleProjects", consultem outros contextos de interface do usuário conhecida (por seus GUIDs). A terceira condição, "DotConfig" é o contexto de interface de usuário baseada em regras definidas anteriormente.  
  
## <a name="delayed-activation"></a>Ativação atrasada  
 Regras podem ter um "atraso" opcional. O atraso é especificado em milissegundos. Se estiver presente, o atraso faz com que a ativação ou desativação de contexto de interface do usuário da regra deve ser atrasada por esse intervalo de tempo. Se as alterações de regra de volta antes do intervalo de atraso, em seguida, nada acontecerá. Esse mecanismo pode ser usado para "balancear" as etapas de inicialização - especialmente a inicialização única sem depender de temporizadores ou se registrar para notificações ociosas.  
  
 Por exemplo, você pode especificar sua regra de carga de teste para ter um atraso de 100 milissegundos:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Tipos de termo  
 Aqui estão os vários tipos de termo que têm suporte:  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|O GUID se refere a um contexto de interface do usuário. O termo será verdadeiro sempre que o contexto da interface do usuário está ativo e FALSO caso contrário.|  
|HierSingleSelectionName:\<padrão >|O termo será verdadeiro sempre que a seleção na hierarquia de ativo é um único item e o nome do item selecionado corresponde à expressão regular do .net fornecida pelo "padrão".|  
|UserSettingsStoreQuery:\<consulta >|"consulta" representa um caminho completo para o repositório de configurações do usuário que deve ser avaliada como um valor diferente de zero. A consulta é dividida em uma "coleção" e "propertyName" no último barra.|  
|ConfigSettingsStoreQuery:\<consulta >|"consulta" representa um caminho completo para o repositório de configurações de configuração que deve ser avaliada como um valor diferente de zero. A consulta é dividida em uma "coleção" e "propertyName" no último barra.|  
|ActiveProjectFlavor:\<projectTypeGuid >|O termo será verdadeiro sempre que o projeto selecionado no momento é versão (agregado) e tem um tipo correspondente ao tipo de projeto fornecido GUID.|  
|ActiveEditorContentType:\<contentType >|O termo será verdadeiro quando o documento selecionado é um editor de texto com o tipo de conteúdo fornecido.|  
|ActiveProjectCapability:\<expressão >|O termo é verdadeiro quando os recursos de projeto ativo corresponde à expressão fornecida. Uma expressão pode ser algo como VB &#124; CSharp|  
|SolutionHasProjectCapability:\<expressão >|Semelhante aos acima, mas termo é verdadeiro quando a solução tem qualquer projeto carregado que corresponde à expressão.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|O termo será verdadeiro sempre que uma solução teve o projeto é a versão (agregado) e tem um tipo correspondente ao tipo de projeto fornecido GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Compatibilidade com extensão entre versões  
 Regra baseado em contextos de interface do usuário é um novo recurso no Visual Studio 2015 e não deve ser movido para versões anteriores. Isso cria um problema com extensões/pacotes destinados a várias versões do Visual Studio que teria de ser carregado automaticamente no Visual Studio 2013 e anteriores, mas pode se beneficiar de regra com base em contextos de interface do usuário para evitar que está sendo carregado automaticamente no Visual Studio 2015.  
  
 Para oferecer suporte a esses pacotes, AutoLoadPackages entradas no registro agora podem fornecer um sinalizador em seu campo de valor para indicar que a entrada deve ser ignorada no Visual Studio 2015 e superior. Isso pode ser feito adicionando uma opção de sinalizadores <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. VSPackages agora pode adicionar **SkipWhenUIContextRulesActive** opção para seus <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo para indicar a entrada deve ser ignorada no Visual Studio 2015 e superior.  
  
## <a name="extensible-ui-context-rules"></a>Regras de contexto de interface do usuário extensível  
 Às vezes, os pacotes não podem usar regras estáticas do contexto de interface do usuário. Por exemplo, suponha que você tenha um pacote de extensibilidade de suporte, de modo que o estado do comando é baseado nos tipos de editor que são suportados por provedores MEF importados. O comando será habilitado se há uma extensão que suporte o tipo de edição atual. Nesses casos o próprio pacote não é possível usar uma regra estática do contexto de interface do usuário, desde que os termos seriam alterados dependendo de qual MEF extensões estão disponíveis.  
  
 Para oferecer suporte a esses pacotes, contextos de interface do usuário com base em regra oferecem suporte a uma expressão codificada "*" que indica todos os termos abaixo será associado com ou. Isso permite que o pacote mestre definir uma regra conhecida com base em contexto de interface do usuário e vincular seu estado de comando para este contexto. Depois qualquer extensão MEF direcionado para o pacote mestre pode adicionar seus termos para editores que ele suporta sem afetar outros termos ou a expressão mestre.  
  
 O construtor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentação mostra a sintaxe para regras de contexto de interface do usuário extensíveis.