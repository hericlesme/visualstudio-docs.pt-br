---
title: Projeto de amostra para criar um adaptador de dados de diagnóstico no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 98606c5afbeed035392f35d71de60bb4d4bbb5a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Projeto de amostra para criar um adaptador de dados de diagnóstico

"MyDiagnosticDataAdapter" é um adaptador de dados de diagnóstico simples que pode anexar um arquivo de log aos resultados do teste quando você executa testes.

 Você precisará de permissões administrativas em qualquer computador onde o coletor de dados de diagnóstico ou o editor de configuração estiverem instalados.

## <a name="example-data-adapter"></a>Adaptador de dados de exemplo

Este exemplo demonstra como realizar as seguintes tarefas:

-   Aplicar atributos para tornar uma classe detectável pelo Microsoft Test Manager como um adaptador de dados de diagnóstico.

-   Aplicar atributos para tornar uma classe de controle de usuário detectável pelo Microsoft Test Manager como um editor a ser usado para alterar a configuração de um adaptador de dados de diagnóstico.

-   Acessar dados de configuração padrão.

-   Registrar-se para eventos específicos da Coleção de Dados de Diagnóstico.

-   Anexar o arquivo de log enviando-o para <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>Editor de configuração de exemplo

Este é um editor de configuração de exemplo para o adaptador de dados de diagnóstico. Adicione um controle de usuário ao seu projeto e crie um formulário muito simples que tenha um rótulo ("Nome do arquivo de log:") e uma caixa de texto chamada "FileTextBox".

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

            string result = String.Empty;
            if (files.Count > 0)
            {
                XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result = pathAttribute.Value;
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-file"></a>Arquivo de configuração de exemplo

Veja a seguir um exemplo de arquivo de configuração para seu editor de configuração do coletor de dados de diagnóstico.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>Compilando o código

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>Para criar o projeto de código para este adaptador de diagnóstico

1.  Crie um novo projeto de biblioteca de classes chamado "MyDataCollector".

2.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e escolha **Propriedades**. Para selecionar uma pasta a ser adicionada, escolha **Caminhos de Referência** e escolha as reticências (**…**).

     A caixa de diálogo **Selecionar Caminho de Referência** é exibida.

3.  Selecione o seguinte caminho, com base no diretório de instalação: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Escolha **OK**.

4.  Para adicionar a pasta ao caminho de referência, escolha **Adicionar Pasta**.

     A pasta é exibida na lista de caminhos de referência.

5.  Escolha o ícone **Salvar Tudo** para salvar os caminhos de referência.

6.  Adicione o assembly **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Referências** e escolha **Adicionar Referência**.

    2.  Escolha **Procurar** e localize **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Esse assembly será encontrado em *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Escolha **OK**.

7.  Adicione o assembly **Microsoft.VisualStudio.QualityTools.Common**.

    1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **Referências** e selecione **Adicionar Referência**.

    2.  Escolha **Procurar** e localize **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Esse assembly será encontrado em *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Escolha **OK**.

8.  Copie a classe do adaptador de dados de diagnóstico listada anteriormente neste documento na classe da sua biblioteca de classes. Salve essa classe.

9. Para adicionar um controle de usuário ao projeto, clique com o botão direito do mouse no projeto MyDataCollector no Gerenciador de Soluções, aponte para **Adicionar** e escolha **Controle do Usuário**. Escolha **Adicionar**.

10. Usando a Caixa de Ferramentas, adicione um rótulo ao controle de usuário e altere a propriedade Texto para **Nome de Arquivo:**.

11. Usando a Caixa de Ferramentas, adicione uma caixa de texto ao controle de usuário e altere o nome para **textBoxFileName**.

12. No **Gerenciador de Soluções**, clique com o botão direito do mouse no controle de usuário e escolha **Exibir Código**. Substitua essa classe do controle de usuário pela classe do controle de usuário que foi listada anteriormente neste documento. Salve essa classe.

    > [!NOTE]
    > Por padrão, o controle de usuário é chamado UserControl1. Verifique se o código de classe do controle de usuário usa o nome do seu controle de usuário.

13. Para criar o arquivo de configuração, no **Gerenciador de Soluções**, clique com o botão direito do mouse na solução, aponte para **Adicionar** e escolha **Novo Item**. Opte por selecionar **Arquivo de Configuração de Aplicativo** e, em seguida, escolha **Adicionar**. Isso adicionará um arquivo chamado **App.config** à sua solução.

14. Copie o XML do exemplo que foi fornecido antes no arquivo XML. Salve o arquivo.

15. Compile a solução e copie o assembly compilado e o arquivo `App.config` no diretório *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

16. Crie configurações de teste que usem esse adaptador de diagnóstico de dados personalizado. Defina as configurações de teste para coletar um arquivo que existe.

     Se estiver executando seus testes no Microsoft Test Manager, você poderá atribuir essas configurações de teste ao seu plano de teste antes de executar os testes ou usar o comando Executar com opções para atribuir e substituir configurações de teste. Para obter mais informações sobre as configurações de teste, consulte [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md).

17. Execute os testes usando as configurações de teste com o adaptador de dados de diagnóstico selecionado.

     O arquivo de dados que você especificou será anexado aos resultados do teste quando o teste for executado.

## <a name="see-also"></a>Consulte também

- [Como criar um adaptador de dados de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Como criar um editor personalizado para dados para o adaptador de dados de diagnóstico](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Como instalar um adaptador de dados de diagnóstico personalizado](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Criando um adaptador de dados de diagnóstico para coletar dados personalizados ou afetar um computador de teste](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)