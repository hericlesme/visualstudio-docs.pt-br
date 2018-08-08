---
title: Criar um editor de dados personalizado para um adaptador de dados de diagnóstico no Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e46b8af413f7f86592ed6c9362ca9f11e61c436f
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380372"
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Como criar um editor personalizado de dados para o adaptador de dados de diagnóstico

Ao criar um adaptador de dados de diagnóstico, talvez você queira permitir que o usuário final configure dados específicos quando o adaptador de dados de diagnóstico personalizado for selecionado para suas configurações de teste. Por exemplo, você pode selecionar os dados da configuração que especificam quais chaves do Registro extrair, que nível de carga de rede simular ou em que diretório encontrar arquivos temporários ou de trabalho a serem anexados.

Você deve usar um arquivo de configuração para definir valores iniciais para o adaptador de dados de diagnóstico. Você pode fornecer um editor personalizado para permitir que o usuário modifique os dados de configuração.

Para criar seu próprio editor, você criará um controle de usuário que implementa <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

O adaptador de dados de diagnóstico pode usar um <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> para especificar a classe do editor a ser usada na edição das configurações de dados de diagnóstico.

Você também especifica os dados de configuração padrão que deseja usar.  Confira [Projeto de exemplo para criação de um adaptador de dados de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md) para obter uma configuração padrão de exemplo.

Use o seguinte procedimento para criar um editor personalizado a fim de atualizar dados das configurações de teste quando o adaptador de diagnóstico de dados personalizado for usado.

> [!NOTE]
> Para criar um editor personalizado, você deve primeiro criar o adaptador de dados de diagnóstico que tem <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> aplicado à classe. Você pode usar a propriedade opcional <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> nesse atributo para especificar a fonte de conteúdo da ajuda para seu editor. Para obter mais informações sobre como criar o adaptador de dados de diagnóstico, confira [Como criar um adaptador de dados de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md).

Para obter um projeto completo do adaptador de dados de diagnóstico de exemplo, incluindo um editor de configuração personalizado, confira [Projeto de exemplo para criar um adaptador de dados de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Para criar um editor personalizado para o adaptador de dados de diagnóstico

1.  Crie um controle de usuário no projeto para o adaptador de diagnóstico de dados:

    1.  Clique com o botão direito do mouse no projeto de código que contém sua classe do adaptador de dados de diagnóstico, aponte para **Adicionar** e para **Controle do Usuário**.

    2.  Para este exemplo, adicione um rótulo ao formulário com este texto: **Nome do Arquivo de Dados:** e uma caixa de texto chamada **FileTextBox** que permitirá que o usuário insira os dados necessários.

    > [!NOTE]
    > Apenas os controles de usuário do Windows Forms são compatíveis no momento.

2.  Adicione essas linhas à seção de declaração:

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Crie este controle de usuário em um editor personalizado.

    1.  Clique com o botão direito do mouse no controle de usuário em seu projeto de código e aponte para **Exibir código**.

    2.  Defina a classe para implementar a interface <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> do editor, da seguinte forma:

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Clique com o botão direito do mouse em <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> no código e selecione o comando **Implementar Interface**. Os métodos que você deve implementar para essa interface são adicionados à classe.

    2.  Adicione <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> ao controle de usuário para que o editor identifique-o como um editor do adaptador de dados de diagnóstico, substituindo **Empresa**, **Produto** e **Versão** pelas informações apropriadas ao adaptador de dados de diagnóstico:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Adicione duas variáveis particulares da seguinte forma:

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Adicione código para inicializar seu editor para o adaptador de dados de diagnóstico. Você pode adicionar valores padrão para os campos no controle de usuário usando os dados que estão na variável de configurações. Esses são os dados que estão no elemento `<DefaultConfiguration>` do arquivo de configuração XML para o adaptador.

    ```csharp
    public void Initialize(
        IServiceProvider svcProvider,
        DataCollectorSettings settings)
    {
        ServiceProvider = svcProvider;
        collectorSettings = settings;

        // Display the default file name as listed in the settings file.
        this.SuspendLayout();
        this.FileTextBox.Text = getText(collectorSettings.Configuration);
        this.ResumeLayout();
    }
    ```

6.  Adicione código para salvar os dados dos controles no editor novamente no formato XML exigido pela API do adaptador de dados de diagnóstico da seguinte forma:

    ```csharp
    public DataCollectorSettings SaveData()
    {
        collectorSettings.Configuration.InnerXml =
            String.Format(
    @"<MyCollectorName
        xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
      <File FullPath=""{0}"" />
    </MyCollectorName>",
        FileTextBox.Text);
        return collectorSettings;
    }
    ```

7.  Se for importante para você, adicione código para verificar se os dados estão corretos no método `VerifyData` ou você poderá fazer o método retornar `true`.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  (Opcional) Você pode adicionar código para redefinir os dados das configurações iniciais que são fornecidas no arquivo de configuração XML no método de `ResetToAgentDefaults()` que usa o método particular `getText()`.

    ```csharp
    // Reset to default value from XML configuration
    // using a custom getText() method
    public void ResetToAgentDefaults()
    {
        this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
    }

    // Local method to read the configuration settings
    private string getText(XmlElement element)
    {
        // Setup namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                element.OwnerDocument.NameTable);

        // Find all the "File" elements under our configuration
        XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

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
    ```

9. Compile sua solução. Copie o assembly do adaptador de diagnóstico de dados e o arquivo de configuração XML (`<diagnostic data adapter name>.dll.config`) para o local a seguir com base no diretório de instalação: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Embora o editor de configuração possa estar em um projeto e um assembly que é diferente do adaptador de dados de diagnóstico, eles também podem estar no mesmo assembly.

10. Para usar o adaptador de dados de diagnóstico em testes, você deve selecionar na lista de configurações de teste existente ou criar um novo do Microsoft Test Manager ou do Visual Studio e selecionar o adaptador de dados de diagnóstico.

     O adaptador é exibido na guia **Dados e Diagnósticos** das configurações de teste com o nome amigável que você atribuiu à classe.

11. Para configurar o adaptador de dados de diagnóstico para suas configurações de teste, escolha **Configurar** próximo ao nome do adaptador.

     O editor personalizado é exibido agora.

12. Edite os campos em seu editor personalizado conforme necessário e escolha **Salvar**.

13. Se estiver executando seus testes no Microsoft Test Manager, você poderá atribuir essas configurações de teste ao seu plano de teste antes de executar os testes ou usar o comando **Executar com opções** para atribuir e substituir configurações de teste. Para obter mais informações sobre as configurações de teste, confira [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md).

14. Para que seja possível usar o novo editor de configuração com um adaptador de dados de diagnóstico, você deve aplicar <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> a cada classe do adaptador de dados de diagnóstico que você deseja usar o editor e recompilá-las e reinstalá-las no computador cliente. Para obter mais informações sobre como instalar adaptadores de dados de diagnóstico e editores de configuração, confira [Como instalar um adaptador de dados de diagnóstico personalizado](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Execute seus testes usando as configurações de teste com o adaptador de dados de diagnóstico selecionado.

     O arquivo de dados que você especificou no editor está anexado aos resultados do teste.

 Para obter mais informações sobre como definir suas configurações de teste para usar um ambiente quando executar testes, consulte [Coletar dados de diagnóstico em testes manuais (VSTS)](/vsts/manual-test/collect-diagnostic-data) ou [Coletar dados de diagnóstico durante testes (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Criar um adaptador de dados de diagnóstico para coletar dados personalizados ou afetar um computador de teste](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md)
- [Projeto de amostra para criar um adaptador de dados de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)