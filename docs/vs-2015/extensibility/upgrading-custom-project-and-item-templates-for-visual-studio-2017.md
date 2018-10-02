---
title: Atualizando modelos de Item e projeto personalizados para o Visual Studio "15" | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02c7b14051a41616ed1b98812d1f1b7762f7165e
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "47587917"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>Atualizando modelos de Item e projeto personalizados para o Visual Studio "15"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [atualizando personalizados de projeto e modelos de Item para Visual Studio ](https://docs.microsoft.com/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017).  
  
A partir do Visual Studio "15" visualização 4, o Visual Studio está mudando a maneira como ele descobre que os modelos de projeto e item que foram instalados por um VSIX ou um. msi. Se você possui as extensões que usam modelos de item ou de projeto personalizado, você precisará atualizar suas extensões. Este tópico explica o que você deve fazer.  
  
 Essa alteração afeta apenas o Visual Studio "15". Ele não afeta as versões anteriores do Visual Studio.  
  
 Se você quiser criar um modelo de projeto ou item como parte de uma extensão do VSIX, consulte [personalizados de criação de projeto e modelos de Item](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Verificação de modelo  
 Anteriormente, **devenv /setup** ou **devenv /installvstemplates** verificados no disco local para localizar modelos de projeto e item. Começando na visualização 4, verificação será executada somente para o nível de usuário local (**%USERPROFILE%\Documents\\< versão do Visual Studio\>\My Exported Templates\\**) que é usado para modelos gerados pelo **arquivo / exportar modelos** comando.  
  
 Para outros locais (não-usuário), você deve incluir um arquivo de manifest(.vstman) que especifica o local e outras características do modelo. O arquivo vstman é gerado, juntamente com o arquivo. vstemplate usado para modelos. Se você instalar a extensão usando um. VSIX, você pode fazer isso por meio da recompilação a extensão do Visual Studio "15" Preview 2. Mas se você usar um. msi, você precisa fazer as alterações manualmente. Para obter uma lista do que você precisa fazer para que essas alterações, consulte **atualizações para extensões instaladas com um. MSI** mais adiante neste tópico.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Como atualizar uma extensão do VSIX com modelos de Item ou projeto  
 Este procedimento explica como fazer a atualização do Visual Studio "15" Preview 2 sua extensão do VSIX existente.  
  
1.  Abra a solução no Visual Studio "15" Preview 2. Você será solicitado a atualizar o código. Clique em **OK**.  
  
2.  Após a conclusão da atualização, você precisa alterar a versão de destino de instalação. No projeto VSIX, abra o arquivo vsixmanifest e selecione o **instalar destinos** guia. Se o **intervalo de versão** campo é **[14.0]**, clique em **editar** e alterá-lo para incluir o Visual Studio "15". Por exemplo, ele pode ser definido como **[14.0,15.0]** para instalar a extensão do Visual Studio 2015 ou Visual Studio "15", ou em **[15.0]** para instalá-lo para apenas o Visual Studio "15".  
  
3.  Recompile o código.  
  
4.  Feche o Visual Studio.  
  
5.  Instale o VSIX.  
  
6.  Você pode testar a atualização, fazendo o seguinte:  
  
    1.  Verificação de alteração de arquivo é ativado pela seguinte chave do registro:  
  
         **reg adicionar hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Depois de adicionar a chave, execute **devenv /installvstemplates**.  
  
    3.  Reabra o Visual Studio. Você deve encontrar o modelo no local esperado.  
  
    > [!NOTE]
    >  Os modelos de projeto de extensibilidade do Visual Studio não estão disponíveis quando a chave do registro está presente. Você deve excluir a chave do registro (e executar novamente **devenv /installvstemplates**) para usá-los.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Outras recomendações para a implantação de modelos de projeto e Item  
  
-   Evite usar arquivos de modelo compactado. Compactado arquivos precisam ser descompactado para recuperar os recursos e o conteúdo do modelo, portanto, eles serão mais caras usar. Em vez disso, você deve implantar os modelos de projeto e item como arquivos individuais em seu próprio diretório para acelerar a inicialização de modelo. Extensões de VSIX, tarefas de build do SDK descompactará automaticamente qualquer modelo compactado ao criar o arquivo VSIX.  
  
-   Evite usar entradas de ID de recurso do pacote para o nome do modelo, a descrição, o ícone ou a visualização para evitar cargas de assembly de recurso desnecessárias durante a descoberta de modelo. Em vez disso, você pode usar manifestos localizados para criar uma entrada de modelo para cada localidade, que usa nomes localizados ou propriedades.  
  
-   Se você estiver incluindo modelos como itens de arquivo, geração de manifesto não pode fornecer os resultados esperados. Nesse caso, você terá que adicionar um manifesto gerado manualmente para o projeto VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Alterações de arquivo no projeto e modelos de Item  
 Mostraremos os pontos da diferença entre a versão do Visual Studio 2015 e a versão do Visual Studio "15" dos arquivos de modelo, para que você possa criar novos arquivos corretamente.  
  
 Aqui está o arquivo. vstemplate de projeto padrão criado pelo Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Aqui está o arquivo de vstman (você pode encontrá-lo no diretório de manifesto do projeto VSIX) que resultaram da recriação do projeto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 As informações fornecidas pelo [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento permanece o mesmo. O  **\<VSTemplateContainer >** elemento aponta para o arquivo. vstemplate para o modelo associado.  
  
 Aqui está o arquivo. vstemplate de item de padrão criado pelo Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Aqui está o arquivo de vstman (você pode encontrá-lo no diretório de manifesto do projeto VSIX) que resultaram da recriação do projeto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 As informações fornecidas pelo  **\<TemplateData >** elemento permanece o mesmo. O  **\<VSTemplateContainer >** elemento aponta para o arquivo. vstemplate para o modelo associado  
  
 Para obter mais informações sobre os diferentes elementos do arquivo vstman, consulte [modelo de manifesto do esquema de referência do Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Atualizações para as extensões instaladas com um. MSI  
 Algumas extensões baseadas em MSI Implante modelos locais de modelo comuns, como o seguinte:  
  
-   **\<Diretório de instalação do Visual Studio > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**  
  
-   **\<Diretório de instalação do Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project/ItemTemplates >**  
  
 Se sua extensão executa uma implantação baseada em MSI, você precisa gerar o manifesto do modelo manualmente e certifique-se de que ele seja incluído na configuração da extensão. Você deve comparar os exemplos de vstman listados acima e o [modelo de manifesto do esquema de referência do Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md). Para ver o que você precisa incluir  
  
 Você deve criar manifestos separados para modelos de projeto e item, e eles devem apontar para o modelo diretório raiz conforme especificado acima. Você deve criar um manifesto por extensão e a localidade.  
  
## <a name="troubleshooting-template-installation"></a>Instalação do modelo de solução de problemas  
 Se você tiver problemas ao implantar seus modelos de projeto ou item, você pode habilitar o log de diagnóstico.  
  
1.  Execute o seguinte comando para definir a chave do registro para habilitar o registro em log:  
  
     **reg adicionar HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Inicie o Visual Studio e inicie as caixas de diálogo New Project e o novo Item para inicializar a ambas as árvores do modelo. O log de modelo agora aparece na **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. A inicialização de cada árvore modelo acrescenta as entradas nesse log.  
  
 O arquivo de log contém as seguintes colunas:  
  
-   **FullPathToTemplate**, que tem os seguintes valores:  
  
    -   1 para implantação baseada em manifesto  
  
    -   0 para implantação baseada em disco  
  
-   **TemplateFileName**  
  
-   Outras propriedades de modelo

