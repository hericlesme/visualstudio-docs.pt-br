---
title: Configurar testes de unidade no Visual Studio com um arquivo .runsettings | Microsoft Docs
ms.date: 02/28/2018
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3a446c3223197058401e07a5aef2cb13bde46f3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurar testes de unidade usando um *.runsettings*

Os testes de unidade no Visual Studio podem ser configurados com um arquivo *.runsettings*. Por exemplo, é possível alterar a versão do .NET Framework em que os testes são executados, o diretório para os resultados do teste ou os dados coletados durante execução de um teste.

> [!NOTE]
> O nome do arquivo não importa, desde que você use a extensão '.runsettings'.

Se você não precisar de nenhuma configuração especial, não será necessário ter um arquivo *.runsettings*. O uso mais comum de um arquivo *.runsettings* é personalizar a [Análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="customize-tests"></a>Personalizar testes

1. Adicione um arquivo XML à solução Visual Studio e renomeie-o para *test.runsettings*.

1. Substitua o conteúdo do arquivo pelo XML do exemplo a seguir e personalize-o conforme o necessário.

1. No menu **Testar**, escolha **Configurações de Teste** > **Selecionar Arquivo de Configurações de Teste**.

É possível criar mais de um arquivo *.runsettings* em sua solução e habilitá-los ou desabilitá-los em momentos diferentes com o menu **Configurações de Teste**.

![Habilitando um arquivo de configurações de execução](../test/media/runsettings-1.png)

## <a name="example-runsettings-file"></a>Arquivo *.runsettings* de exemplo

Veja a seguir um arquivo *.runsettings* típico. Cada elemento do arquivo é opcional, porque cada valor possui um padrão.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

     <!--TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
     <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
     <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

O arquivo *.runsettings* também é usado para configurar a [Análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

O restante deste artigo descreve o conteúdo do arquivo.

## <a name="edit-your-runsettings-file"></a>Editar o arquivo *.runsettings*

As seções a seguir detalham os elementos de um arquivo *.runsettings*.

### <a name="test-run-configuration"></a>Configuração de execução de teste

|Nó|Padrão|Valores|
|----------|-------------|------------|
|`ResultsDirectory`||O diretório no qual os resultados do teste são colocados.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Essa configuração especifica qual versão do framework de testes de unidade é usada para descobrir e executar os testes. Pode ser diferente da versão da plataforma .NET especificada nas propriedades de compilação do projeto de teste de unidade.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|false|false, true|
|`TestAdaptersPaths`||Um ou vários caminhos para o diretório em que os TestAdapters estão localizados|
|`MaxCpuCount`|1|Essa configuração controla o grau de execução de teste paralela ao executar testes de unidade usando os núcleos disponíveis no computador. O mecanismo de execução de testes inicia como um processo distinto em cada núcleo disponível e fornece um contêiner para cada núcleo com testes a serem executados. Um contêiner pode ser um assembly, uma DLL ou um artefato relevante. O contêiner do teste está agendando a unidade. Em cada contêiner, os testes são executados de acordo com a estrutura de teste. Se houver muitos contêineres, à medida que os processos terminarem de executar os testes em um contêiner, eles passarão para o próximo contêiner disponível.<br /><br /> MaxCpuCount pode ser:<br /><br /> n,em que 1 <= n <= número de núcleos: até n processos serão iniciados<br /><br /> n, em que n = qualquer outro valor: o número de processos iniciados será até a quantidade de núcleos disponíveis no computador|
|`TestSessionTimeout`||Permite que os usuários finalizem uma sessão de teste quando ele exceder o tempo limite determinado. Definir um tempo limite assegura que os recursos serão restritos e as sessões de teste serão restritas a um período de tempo. Essa configuração está disponível no **Visual Studio 2017 versão 15.5** e posterior.

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptadores de dados de diagnóstico (coletores de dados)

O elemento `DataCollectors` especifica configurações de adaptadores de dados de diagnóstico. Os adaptadores de dados de diagnóstico coletam informações adicionais sobre o ambiente e o aplicativo em teste. Cada adaptador tem configurações padrão e você só precisará fornecer configurações caso não deseje usar os padrões.

#### <a name="code-coverage-adapter"></a>Adaptador de cobertura de código

O coletor de dados de cobertura de código cria um log das partes do código do aplicativo que foram utilizadas no teste. Para obter mais informações sobre como personalizar as configurações de cobertura de código, consulte [Personalizando análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Coletor de dados de vídeo

O coletor de dados de vídeo captura uma gravação de tela quando os testes são executados. A gravação é útil para solucionar problemas de testes de interface do usuário. O coletor de dados de vídeo está disponível no **Visual Studio 2017 versão 15.5** e posterior.

Para personalizar qualquer outro tipo de adaptador de dados de diagnóstico, você precisa usar um [arquivo de configurações de teste](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

TestRunParameters fornece uma maneira de definir variáveis e valores disponíveis para os testes em tempo de execução. Essas variáveis podem ser acessadas usando o objeto [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx).

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
```

Para usar o TestContext, adicione campo [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx) privado e uma propriedade `TestContext` pública à classe de teste.

### <a name="mstest-run-settings"></a>Configurações de execução do MSTest

Essas configurações são específicas para o adaptador de teste que executa os métodos de teste que têm o atributo `[TestMethod]`.

|Configuração|Padrão|Valores|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|No Visual Studio 2012, o adaptador MSTest foi otimizado para torná-lo mais rápido e mais escalonável. Alguns comportamentos, como a ordem em que os testes são executados, não podem ser exatamente iguais aos de edições anteriores do Visual Studio. Defina esse valor como `true` para usar o adaptador mais antigo de teste.<br /><br /> Por exemplo, você poderá usar essa configuração se tiver um arquivo *app.config* especificado para um teste de unidade.<br /><br /> Recomendamos que você considere refatorar seus testes para permitir o uso do adaptador mais recente.|
|IgnoreTestImpact|false|O recurso de impacto de teste prioriza os testes que são afetados pelas alterações recentes, quando executados no MSTest ou no Microsoft Test Manager. Essa configuração desativa o recurso. Para obter mais informações, consulte [Como coletar dados para verificar quais testes devem ser executados após alterações feitas no código](http://msdn.microsoft.com/Library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Você pode especificar uma arquivo de configurações de teste para usar com o adaptador MSTest aqui. Também é possível especificar um arquivo de configurações de teste usando o menu **Testar**, **Configurações de Teste**, **Selecionar Arquivo de Configurações de Teste**.<br /><br /> Se você especificar esse valor, também será necessário definir o **ForcedlegacyMode** como **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|Após a execução do teste ser concluída, o MSTest será fechado. Qualquer processo iniciado como parte do teste também será eliminado. Se você quiser manter o executor de teste ativo, transforme essa configuração em true.<br /><br /> Por exemplo, você pode usar essa configuração para manter o navegador em execução entre os testes de IU codificados.|
|DeploymentEnabled|true|Se você definir esse valor como false, os itens de implantação especificados em seu método de teste não serão copiados para o diretório de implantação.|
|CaptureTraceOutput|true|Você pode gravar no rastreamento de depuração do método de teste usando Trace.WriteLine. Usando essa configuração, você pode desativar esses rastreamentos de depuração.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Você pode manter o Diretório de Implantação após um teste configurando esse valor para false.|
|MapInconclusiveToFailed|false|Se um teste retornar com um status inconclusivo, ele geralmente será mapeado para o status Ignorado no Gerenciador de Testes. Se você quiser que os testes Inconclusivos sejam mostrados como Falha, use esta configuração.|
|InProcMode|false|Se você quiser que os testes sejam executados no mesmo processo do adaptador MSTest, defina esse valor como true. Essa configuração fornece um ganho menor de desempenho. Mas se um teste fechar com uma exceção, os outros testes não continuarão.|
|AssemblyResolution|false|É possível especificar caminhos para outros assemblies ao localizar e executar testes de unidade. Por exemplo, use esses caminhos para assemblies de dependência que não residem no mesmo diretório que o assembly de teste. Para especificar um caminho, use um elemento de “Caminho do diretório”. Os caminhos podem conter variáveis de ambiente.<br /><br /> `<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Consulte também

- [Personalizando a análise de cobertura de código](../test/customizing-code-coverage-analysis.md)