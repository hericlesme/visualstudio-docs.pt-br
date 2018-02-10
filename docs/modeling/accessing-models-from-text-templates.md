---
title: Acessar modelos de modelos de texto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3162350a9afbe7972c4e593049141f533517bdc3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-models-from-text-templates"></a>Acessando modelos a partir de modelos (templates) de texto
Usando modelos de texto, você pode criar arquivos de relatório, arquivos de código fonte e outros arquivos de texto com base em modelos de linguagem específica de domínio. Para obter informações básicas sobre modelos de texto, consulte [geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md). Os modelos de texto funcionarão no modo de avaliação quando você estiver depurando seu DSL e também funcionará em um computador no qual você implantou o DSL.  
  
> [!NOTE]
>  Quando você cria uma solução DSL, o modelo de texto de exemplo  **\*. TT** arquivos são gerados no projeto de depuração. Quando você altera os nomes das classes de domínio, esses modelos não funcionará mais. No entanto, eles incluem as diretivas básicas que você precisa e fornecem exemplos que você pode atualizar para coincidir com seu DSL.  
  
 Para acessar um modelo de um modelo de texto:  
  
-   Defina a propriedade de herdar da diretiva de modelo para <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Fornece acesso ao repositório.  
  
-   Especifique os processadores de diretiva para DSL que você deseja acessar. Isso carrega os assemblies do seu DSL para que você possa usar suas classes de domínio, propriedades e relações no código do seu modelo de texto. Além disso, ele carrega o arquivo de modelo que você especificar.  
  
 Um `.tt` arquivo semelhante ao exemplo a seguir é criado no projeto de depuração quando você cria um novo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução do modelo de idioma de DSL mínimo.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Observe os seguintes pontos sobre este modelo:  
  
-   O modelo pode usar as classes de domínio, propriedades e relações que você definiu na definição de DSL.  
  
-   O modelo carrega o arquivo de modelo que você especificar o `requires` propriedade.  
  
-   Uma propriedade em `this` contém o elemento raiz. A partir daí, seu código pode navegar para outros elementos do modelo. O nome da propriedade normalmente é o mesmo que a classe de domínio raiz de seu DSL. Neste exemplo, é `this.ExampleModel`.  
  
-   Embora o idioma no qual são gravados os fragmentos de código c#, você pode gerar o texto de qualquer tipo. Como alternativa você pode escrever o código em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] adicionando a propriedade `language="VB"` para o `template` diretiva.  
  
-   Para depurar o modelo, adicione `debug="true"` para o `template` diretiva. O modelo será aberto em outra instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se ocorrer uma exceção. Se você quiser invadir o depurador em um ponto específico no código, a instrução insert`System.Diagnostics.Debugger.Break();`  
  
     Para obter mais informações, consulte [depurando um modelo de texto T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Sobre o processador de diretiva DSL  
 O modelo pode usar as classes de domínio que você definiu em sua definição de DSL. Isso é colocado uma diretiva que normalmente aparece próximo do início do modelo. No exemplo anterior, é o seguinte.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 O nome da diretiva ( `MyLanguage`, neste exemplo) é derivado do nome do seu DSL. Invoca um *processador de diretiva* que é gerado como parte de seu DSL. Você pode encontrar o seu código-fonte em **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 O processador de diretiva DSL executa duas tarefas principais:  
  
-   Ele insere efetivamente diretivas de assembly e importação para o modelo que faz referência a seu DSL. Isso lhe permite usar as classes de domínio no código de modelo.  
  
-   Ele carrega o arquivo que você especificar na `requires` parâmetro e define uma propriedade `this` que faz referência ao elemento raiz do modelo carregado.  
  
## <a name="validating-the-model-before-running-the-template"></a>Validação do modelo antes de executar o modelo  
 Você pode fazer o modelo a ser validada antes do modelo é executado.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Observe que:  
  
1.  O `filename` e `validation` parâmetros são separados por ";" e não deve haver nenhuma outra separadores ou espaços.  
  
2.  A lista de categorias de validação determina quais métodos de validação serão executados. Várias categorias devem ser separadas por "&#124;" e não deve haver nenhuma outra separadores ou espaços.  
  
 Se um erro for encontrado, ele será relatado na janela de erros e o arquivo de resultado conterá uma mensagem de erro.  
  
##  <a name="Multiple"></a>Acessando vários modelos em um modelo de texto  
  
> [!NOTE]
>  Esse método permite que você leia vários modelos no mesmo modelo, mas não oferece suporte a referências de ModelBus. Para ler os modelos que são interligados por ModelBus referências, consulte [usando o Visual Studio ModelBus em um modelo de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Se você quiser acessar mais de um modelo a partir do mesmo modelo de texto, você deve chamar o processador de diretiva gerado uma vez para cada modelo. Você deve especificar o nome do arquivo de cada modelo no `requires` parâmetro. Você deve especificar os nomes que você deseja usar para a classe de domínio raiz no `provides` parâmetro. Você deve especificar valores diferentes para o `provides` parâmetros de cada uma das chamadas diretivas. Por exemplo, suponha que você tenha três arquivos de modelo chamados Library.xyz, School.xyz e Work.xyz. Para acessá-los a partir do mesmo modelo de texto, você deve gravar três chamadas diretivas semelhantes às seguintes.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Esse código de exemplo é para um idioma que é baseado no modelo de solução de idioma mínimo.  
  
 Para acessar os modelos no modelo de texto, agora você pode escrever código semelhante ao código no exemplo a seguir.  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>Carregando modelos dinamicamente  
 Se você quiser determinar em tempo de execução que modelos para carregar, você pode carregar um arquivo de modelo dinamicamente em seu código de programa, em vez de usar a diretiva de DSL específicos.  
  
 No entanto, uma das funções da diretiva DSL específica é importar o namespace DSL, para que o código de modelo pode usar as classes de domínio definidas que DSL. Porque você não estiver usando a diretiva, você deve adicionar  **\<assembly >** e  **\<Importar >** diretivas para todos os modelos que você pode carregar. Isso é fácil se os modelos diferentes que você pode carregar todas as instâncias do mesmo DSL.  
  
 Para carregar o arquivo, o método mais eficaz é usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. Em um cenário típico, o modelo de texto usará uma diretiva DSL específicas ao carregar o primeiro modelo como de costume. Esse modelo deveria conter referências de ModelBus para outro modelo. Você pode usar ModelBus para abrir o modelo de referência e acessar um elemento específico. Para obter mais informações, consulte [usando o Visual Studio ModelBus em um modelo de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Em um cenário menos comum, você talvez queira abrir um arquivo de modelo para o qual você tem apenas um nome de arquivo, e que talvez não seja atual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Nesse caso, você pode abrir o arquivo usando a técnica descrita no [como: abrir um modelo de arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Gerar vários arquivos de um modelo  
 Se você quiser gerar um vários arquivos - por exemplo, para gerar um arquivo separado para cada elemento em um modelo, há várias abordagens. Por padrão, somente um arquivo é produzido de cada arquivo de modelo.  
  
### <a name="splitting-a-long-file"></a>Dividindo um arquivo longo  
 Nesse método, você pode usar um modelo para gerar um único arquivo, separado por um delimitador. Em seguida, dividir o arquivo em suas partes. Há dois modelos, primeiro para gerar o arquivo único e o outro para dividi-la.  
  
 **LoopTemplate.t4** gera o único arquivo longo. Observe que a sua extensão de arquivo é ".t4", porque ele não deve ser processado diretamente quando você clica em **transformar todos os modelos de**. Este modelo assume um parâmetro, que especifica a cadeia de caracteres de delimitador que separa os segmentos:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt`invoca `LoopTemplate.t4`e, em seguida, divide o arquivo resultante em seus segmentos. Observe que este modelo não tem como um modelo de modelagem, porque ela não lê o modelo.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```