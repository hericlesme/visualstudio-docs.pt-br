---
title: Criar um Kit de desenvolvimento de Software | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55b62ac0ac448023793f511389146ebb1b07da0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109172"
---
# <a name="creating-a-software-development-kit"></a>Criar um Software Development Kit
Um software development kit (SDK) é um conjunto de APIs que você pode fazer referência como um único item no Visual Studio. O **Gerenciador de referências** caixa de diálogo lista todos os SDKs que são relevantes para o projeto. Quando você adiciona um SDK a um projeto, as APIs estão disponíveis no Visual Studio.  
  
 Há dois tipos de SDKs:  
  
-   SDKs de plataforma são componentes obrigatórios para o desenvolvimento de aplicativos para uma plataforma. Por exemplo, o [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK é necessário para desenvolver [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.  
  
-   SDKs de extensão são componentes opcionais que estendem uma plataforma, mas não obrigatório para o desenvolvimento de aplicativos para a plataforma.  
  
 As seções a seguir descrevem a infra-estrutura geral de como criar um SDK de plataforma e SDKs e um SDK de extensão.  
  
-   [SDKs de plataforma](#PlatformSDKs)  
  
-   [SDKs de extensão](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> SDKs de plataforma  
 Os SDKs de plataforma são necessários para desenvolver aplicativos para uma plataforma. Por exemplo, o [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK é necessário para desenvolver aplicativos para [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Instalação  
 Todos os SDKs de plataforma serão instalado em HKLM\Software\Microsoft\Microsoft SDKs\\\v [TPI] [TPV]\\ @InstallationFolder = [raiz do SDK]. Da mesma forma, o [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK está instalado em HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Layout  
 Os SDKs de plataforma terá o layout do seguinte:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Nó|Descrição|  
|----------|-----------------|  
|Pasta Referências|Contém binários que contêm as APIs que podem ser codificados em. Isso pode incluir arquivos de metadados do Windows (WinMD) ou assemblies.|  
|Pasta DesignTime|Contém os arquivos que são necessários somente em tempo de pré-execução/depuração. Isso pode incluir documentos XML, bibliotecas, cabeçalhos, binários de tempo de design da caixa de ferramentas, MSBuild artefatos e assim por diante<br /><br /> Documentos XML devem, idealmente, ser colocados na pasta \DesignTime, mas a documentos XML para referências continuarão a ser posicionados junto com o arquivo de referência no Visual Studio. Por exemplo, o documento XML para uma referência \References\\[configuração]\\[arch]\sample.dll será \References\\[configuração]\\[arch]\sample.xml e a versão localizada do que documentos sejam \References\\[configuração]\\[arch]\\[locale]\sample.xml.|  
|Pasta de configuração|Pode haver apenas três pastas: depuração, varejo e CommonConfiguration. Os autores do SDK podem colocar seus arquivos em CommonConfiguration se o mesmo conjunto de arquivos do SDK deve ser consumido, independentemente da configuração que o consumidor do SDK têm como destino.|  
|Pasta de arquitetura|Pode haver qualquer pasta de arquitetura com suporte. Visual Studio oferece suporte as arquiteturas seguintes: x86, x64, ARM e neutral. Observação: Win32 mapeia para x86 e AnyCPU mapeia para neutro.<br /><br /> MSBuild procura somente sob \CommonConfiguration\neutral SDKs de plataforma.|  
|SDKManifest.xml|Esse arquivo descreve como o Visual Studio deve consumir o SDK. Examinar o manifesto do SDK para [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** o valor que o Pesquisador de objetos exibe na lista de pesquisa.<br /><br /> **PlatformIdentity:** a existência desse atributo informa ao Visual Studio e o MSBuild o SDK é uma plataforma SDK e que as referências adicionadas dele não devem ser copiadas localmente.<br /><br /> **TargetFramework:** este atributo é usado pelo Visual Studio para garantir que apenas projetos direcionados as estruturas mesmo conforme especificado no valor desse atributo pode consumir o SDK.<br /><br /> **MinVSVersion:** este atributo é usado pelo Visual Studio para consumir apenas os SDKs que se aplicam a ele.<br /><br /> **Referência:** esse atributo deve ser especificado para apenas essas referências que contêm controles. Para obter informações sobre como especificar se uma referência contém controles, consulte abaixo.|  
  
##  <a name="ExtensionSDKs"></a> SDKs de extensão  
 As seções a seguir descrevem o que você precisa fazer para implantar uma extensão SDK.  
  
### <a name="installation"></a>Instalação  
 SDKs de extensão podem ser instalados para um usuário específico ou para todos os usuários sem especificar uma chave do registro. Para instalar um SDK para todos os usuários, use o seguinte caminho:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Para uma instalação específica do usuário, use o seguinte caminho:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Se você quiser usar um local diferente, você deve fazer uma das duas coisas:  
  
1.  Especificá-lo em uma chave do registro:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     e adicione uma subchave (padrão) que tem um valor de `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Adicionar a propriedade MSBuild `SDKReferenceDirectoryRoot` para o arquivo de projeto. O valor dessa propriedade é uma lista de vírgula delimitada de semi de diretórios em que residem os SDKs de extensão que você deseja referenciar.  
  
### <a name="installation-layout"></a>Layout de instalação  
 SDKs de extensão tem o layout de instalação a seguir:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< Nome_sdk\>\\< Versão_sdk\>: o nome e a versão da extensão do SDK é derivado dos nomes de pasta correspondente no caminho para a raiz do SDK. MSBuild usa essa identidade para encontrar o SDK no disco, e o Visual Studio exibe essa identidade no **propriedades** janela e **Gerenciador de referências** caixa de diálogo.  
  
2.  Pasta de referências: os binários que contêm as APIs. Eles podem ser arquivos de metadados do Windows (WinMD) ou assemblies.  
  
3.  Pasta Redist: os arquivos que são necessários para o tempo de execução/depuração e devem obter empacotados como parte do aplicativo do usuário. Todos os binários devem ser colocados sob \redist\\< config\>\\< arch\>, e os nomes de binários devem ter o seguinte formato para garantir a exclusividade:  **\<empresa >.\< produto >. \<finalidade >. \<extensão >**. Por exemplo, Microsoft.Cpp.Build.dll. Todos os arquivos com nomes que entrem em conflito com nomes de arquivo de outros SDKs (por exemplo, arquivos javascript, css, pri, xaml, png e jpg) devem ser colocados sob \redist\\< config\>\\< arch\> \\< nome_sdk\>\, exceto os arquivos que estão associados com XAML controla. Esses arquivos devem ser colocados sob \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  A pasta DesignTime: os arquivos que são necessários no somente pré-execução/depuração de tempo e não deve ser empacotados como parte do aplicativo do usuário. Eles podem ser documentos XML, bibliotecas, cabeçalhos, binários de tempo de design da caixa de ferramentas, MSBuild artefatos e assim por diante. Qualquer SDK que é destinado para consumo por um projeto nativo deve ter uma *Nome_sdk*.props arquivo. O exemplo a seguir mostra um exemplo desse tipo de arquivo.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     Documentos de referência do XML serão posicionados junto com o arquivo de referência. Por exemplo, o documento de referência XML para o **\References\\< config\>\\< arch\>\sample.dll** assembly é **\References\\ < configuração\>\\< arch\>\sample.xml**, e a versão localizada desse documento é **\References\\< config\>\\< arch\>\\< localidade\>\sample.xml**.  
  
5.  Pasta de configuração: três subpastas: CommonConfiguration, varejo e depuração. Os autores do SDK podem colocar seus arquivos em CommonConfiguration quando o mesmo conjunto de arquivos do SDK deve ser consumido, independentemente da configuração de destino pelo consumidor do SDK.  
  
6.  Pasta de arquitetura: as arquiteturas a seguir são suportadas: x86, x64, ARM, neutro. Win32 mapeia para x86 e AnyCPU mapeia para neutro.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Esse arquivo descreve como o Visual Studio deve consumir o SDK. Confira o exemplo abaixo.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 A lista a seguir fornece os elementos do arquivo.  
  
1.  DisplayName: o valor que aparece no Gerenciador de referências, Gerenciador de soluções, pesquisador de objetos e outros locais na interface do usuário para o Visual Studio.  
  
2.  ProductFamilyName: O geral SDK nome do produto. Por exemplo, o [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK é denominado "Microsoft.WinJS.1.0" e "Microsoft.WinJS.2.0", que pertencem à mesma família da família de produtos SDK, "WinJS". Este atributo permite que o Visual Studio e o MSBuild fazer essa conexão. Se esse atributo não existir, o nome do SDK é usado como o nome de família de produto.  
  
3.  FrameworkIdentity: especifica uma dependência em uma ou mais bibliotecas de componentes de Windows que o valor desse atributo é colocado no manifesto do aplicativo de consumo. Esse atributo é aplicável somente às bibliotecas de componentes do Windows.  
  
4.  TargetFramework: especifica os SDKs que estão disponíveis no Gerenciador de referências e a caixa de ferramentas. Isso é uma lista separada por ponto-e-vírgula de identificadores do framework de destino, por exemplo "do .NET Framework, versão = v 2.0; .NET Framework, versão = v4.5.1". Se várias versões da mesma estrutura de destino for especificadas, o Gerenciador de referências usa a versão mais antiga especificada para fins de filtragem. Por exemplo, se "do .NET Framework, versão = v 2.0; .NET Framework, versão = v4.5.1" for especificado, usará o Gerenciador de referências "do .NET Framework, versão = v 2.0". Se um perfil de estrutura de destino específico for especificado, somente esse perfil será usado o pelo Gerenciador de referência para fins de filtragem. Por exemplo, quando "Silverlight, versão = v 4.0, perfil = WindowsPhone" for especificado, somente o perfil do Windows Phone; filtra Gerenciador de referências um projeto direcionando o Silverlight 4.0 Framework completo não vê o SDK no Gerenciador de referência.  
  
5.  MinVSVersion: o Visual Studio versão mínima.  
  
6.  MaxPlatformVerson: A versão da plataforma de destino máximo deve ser usada para especificar as versões de plataforma em que o SDK de extensão não funcionará. Por exemplo, o v 11.0 pacote do Microsoft Visual C++ Runtime deve ser referenciada apenas por projetos do Windows 8. Assim, MaxPlatformVersion do projeto Windows 8 é 8.0. Isso significa que o Gerenciador de referências filtra em tempo de execução do pacote do Microsoft Visual C++ para um projeto do Windows 8.1 e MSBuild gera um erro quando um [!INCLUDE[win81](../debugger/includes/win81_md.md)] projeto faz referência a ele. Observação: este elemento tem suporte a partir [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: especifica os SDKs que estão disponíveis no Gerenciador de referência com a especificação de tipos de projeto do Visual Studio aplicáveis. Nove valores reconhecidos: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, gerenciado e nativo. O autor do SDK pode usar e ("+'), ou ("&#124;"), não ("! ") operadores para especificar exatamente o escopo dos tipos de projeto que se aplicam ao SDK.  
  
     WindowsAppContainer identifica projetos para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.  
  
8.  SupportPrefer32Bit: Valores com suporte são "True" e "False". O padrão é "True". Se o valor é definido como "False", o MSBuild retornará um erro para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projetos (ou um aviso para projetos de área de trabalho) se o projeto que faz referência o SDK tem Prefer32Bit habilitado. Para obter mais informações sobre Prefer32Bit, consulte [página Build, Designer de projeto (c#)](../ide/reference/build-page-project-designer-csharp.md) ou [página de compilação, Designer de projeto (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: uma ponto e vírgula lista delimitada de arquiteturas compatíveis com o SDK. MSBuild exibirá um aviso se não há suporte para a arquitetura do SDK do destino no projeto de consumo. Se esse atributo não for especificado, o MSBuild nunca exibe este tipo de aviso.  
  
10. SupportsMultipleVersions: se esse atributo é definido como **erro** ou **aviso**, MSBuild indica que o mesmo projeto não pode fazer referência a várias versões da mesma família de SDK. Se esse atributo não existe ou é definido como **permitir**, MSBuild não exibe este tipo de erro ou aviso.  
  
11. AppX: Especifica o caminho para os pacotes de aplicativos para a biblioteca de componentes do Windows no disco. Esse valor é passado para o componente de registro da biblioteca de componente do Windows durante a depuração local. A convenção de nomenclatura para o nome do arquivo é  **\<empresa >.\< Produto >. \<Arquitetura >. \<Configuração >. \<Versão >. AppX**. Configuração e arquitetura são opcionais em nome do atributo e o valor do atributo se eles não se aplicam à biblioteca de componente do Windows. Esse valor é aplicável somente às bibliotecas de componentes do Windows.  
  
12. CopyRedistToSubDirectory: especifica onde os arquivos nas pastas \redist devem ser copiados em relação a raiz do pacote de aplicativo (ou seja, o **local do pacote** escolhido no Assistente Criar pacote do aplicativo) e raiz do layout de tempo de execução. O local padrão é a raiz do pacote de aplicativo e o layout de F5.  
  
13. DependsOn: Uma lista de identidades do SDK que definem os SDKs do qual esse SDK depende. Esse atributo é exibido no painel de detalhes do Gerenciador de referência.  
  
14. MoreInfo: a URL para a página da web que fornece ajuda e obter mais informações. Esse valor é usado no link mais informações no painel à direita do Gerenciador de referência.  
  
15. Tipo de registro: Especifica o registro WinMD no manifesto de aplicativo e é necessário para WinMD nativo, que tem uma implementação de contraparte DLL.  
  
16. Referência de arquivo: especificado para apenas essas referências que contém os controles ou WinMDs nativo. Para obter informações sobre como especificar se uma referência contém controles, consulte [especificando o local de itens de caixa de ferramentas](#ToolboxItems) abaixo.  
  
##  <a name="ToolboxItems"></a> Especificar o local dos itens de caixa de ferramentas  
 O elemento ToolBoxItems do esquema SDKManifest.xml especifica a categoria e o local dos itens de caixa de ferramentas na plataforma e SDKs de extensão. Os exemplos a seguir mostram como especificar locais diferentes. Isso é aplicável às referências WinMD ou DLL.  
  
1.  Colocar controles na categoria padrão da caixa de ferramentas.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Colocar controles em um nome de categoria específico.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Colocar controles em nomes de categoria específica.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Colocar controles em nomes de categoria diferente no Visual Studio e de mesclagem.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Enumere controles específicos diferentemente no Blend e o Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Enumerar controles específicos e colocá-los no caminho comum do Visual Studio ou apenas no grupo de todos os controles.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Enumerar controles específicos e mostrar apenas um conjunto específico de ChooseItems sem eles sendo na caixa de ferramentas.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um SDK usando C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Passo a passo: Criando um SDK usando c# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)