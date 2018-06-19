---
title: Adicionar uma extensão do protocolo de idioma do servidor | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb6c82eab6878e99c9840ed593d9b9993056d391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107901"
---
# <a name="adding-a-language-server-protocol-extension"></a>Adicionar uma extensão do protocolo de idioma do servidor

A linguagem de servidor de protocolo LSP () é um protocolo comum, na forma de RPC de JSON v 2.0, usada para fornecer recursos de serviço para vários editores de código de idioma. Usando o protocolo, os desenvolvedores podem gravar um servidor único idioma para fornecer recursos de serviço como IntelliSense, diagnósticos de erros de idioma, localize todas as referências, etc. para vários editores de códigos que dão suporte a LSP. Tradicionalmente, os serviços de idioma no Visual Studio podem ser adicionados ao usar arquivos de gramática TextMate para fornecer funcionalidades básicas, como realce de sintaxe, ou gravando em serviços de idioma personalizado usando o conjunto completo de APIs de extensibilidade do Visual Studio para Fornece dados mais ricas. Agora, há suporte para o LSP oferece uma terceira opção.

![serviço de protocolo de servidor de linguagem no Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocolo de idioma do servidor

Para obter mais informações sobre o próprio protocolo, consulte a documentação [aqui](https://github.com/Microsoft/language-server-protocol). A implementação do Visual Studio idioma do protocolo de servidor está em visualização e suporte deve ser considerado experimental. A versão de visualização está na forma de uma extensão ([visualização do cliente de protocolo de servidor de idioma](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **, mas essa extensão só pode ser instalada na visualização canal do Visual Studio**. Uma versão posterior do Visual Studio inclui suporte interno para o protocolo de servidor de idioma, momento em que o sinalizador de visualização será removido. **Você não deve usar a visualização para fins de produção.**

Para obter mais informações sobre como criar um servidor de idioma de exemplo ou como integrar um servidor existente da linguagem de código do Visual Studio, consulte a documentação [aqui](https://code.visualstudio.com/docs/extensions/example-language-server).

![implementação do protocolo de servidor de idioma](media/lsp-implementation.png)

Este artigo descreve como criar uma extensão do Visual Studio que usa um servidor de idioma LSP. Ele pressupõe que você já tenha desenvolvido para um servidor de idioma LSP e deseja apenas integrá-lo no Visual Studio.

Para obter suporte no Visual Studio, os servidores de idioma podem se comunicar com o cliente (Visual Studio) por meio dos seguintes mecanismos:

* Fluxos de entrada/saída padrão
* Pipes nomeados
* Soquetes

A intenção do LSP e suporte para ele no Visual Studio é serviços integrados de idioma que não fazem parte do produto do Visual Studio. Ele não se destina para estender os serviços de idioma existente (como c#) no Visual Studio. Para estender idiomas existentes, consulte o guia de extensibilidade do serviço de idioma (por exemplo, o [plataforma de compilador .NET "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

## <a name="language-server-protocol-features-supported"></a>Recursos de protocolo de servidor de idioma com suporte

Os seguintes recursos LSP até agora têm suporte no Visual Studio:

Mensagem | Tem suporte no Visual Studio
--- | ---
inicializar | sim
inicializado | sim
desligamento | sim
Sair | sim
$/ cancelRequest | sim
janela/showMessage | sim
window/showMessageRequest | sim
janela/logMessage | sim
evento de telemetria / |
cliente/registerCapability |
cliente/unregisterCapability |
workspace/didChangeConfiguration | sim
workspace/didChangeWatchedFiles | sim
espaço de trabalho/símbolo | sim
workspace/executeCommand | sim
espaço de trabalho/applyEdit | sim
textDocument/publishDiagnostics | sim
textDocument/didOpen | sim
textDocument/didChange | sim
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sim
textDocument/didClose | sim
textDocument/conclusão | sim
conclusão e resolver | sim
textDocument/hover | sim
textDocument/signatureHelp | sim
textDocument/referências | sim
textDocument/documentHighlight |
textDocument/documentSymbol | sim
textDocument/formatação | sim
textDocument/rangeFormatting | sim
textDocument/onTypeFormatting |
textDocument/definição | sim
textDocument/codeAction | sim
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/renomear | sim

## <a name="getting-started"></a>Guia de Introdução

### <a name="create-a-vsix-project"></a>Criar um projeto do VSIX

Para criar uma extensão de serviço de linguagem usando um servidor de idioma LSP, primeiro verifique se você tiver o **desenvolvimento de extensão do Visual Studio** instalada para a instância do VS de carga de trabalho.

Em seguida, crie um novo VSIXProject em branco, navegando para **arquivo** > **novo projeto** > **Visual C#**  >   **Extensibilidade** > **projeto VSIX**:

![Criar projeto vsix](media/lsp-vsix-project.png)

Para a versão de visualização, o suporte a VS LSP será na forma de um VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Os desenvolvedores de extensão que deseja criar uma extensão usando servidores de idioma LSP devem assumir uma dependência neste VSIX. Portanto, os clientes que desejam instalar uma extensão de servidor do idioma **deve primeiro instalar o idioma servidor protocolo cliente visualização VSIX.**

Para definir a dependência do VSIX, abra o designer de manifesto do VSIX para seu VSIX (clicando duas vezes no arquivo de source.extension.vsixmanifest no seu projeto) e navegue até **dependências**:

![Adicionar referência para o cliente de protocolo de servidor de idioma](media/lsp-reference-lsp-dependency.png)

Crie uma nova dependência semelhante ao seguinte:

![definir a dependência de cliente do protocolo de servidor de idioma](media/lsp-define-lsp-dependency.png)

* **Origem**: definida manualmente
* **Nome**: visualização do cliente de protocolo de servidor de idioma
* **Identifier**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Intervalo de versão**: [1.0,2.0)
* **Como a dependência é resolvida**: instalado por usuário
* **URL de download**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> O **baixar URL** devem ser preenchidos para os usuários a instalar sua extensão saibam como instalar a dependência necessária.

### <a name="language-server-and-runtime-installation"></a>Instalação de servidor e o tempo de execução de idioma

Por padrão, as extensões criadas para oferecer suporte a servidores de idioma LSP no Visual Studio não conterá os servidores do idioma ou os tempos de execução necessários para executá-los. Os desenvolvedores de extensão serão responsáveis por distribuir os servidores de idioma e os tempos de execução necessário. Há várias maneiras de fazer isso:

* Servidores de idioma podem ser inseridas em VSIX como arquivos de conteúdo.
* Criar um MSI para instalar o servidor de idioma e/ou necessário tempos de execução.
* Fornece instruções sobre usuários informando do Marketplace como obter servidores tempos de execução e de idioma.

### <a name="textmate-grammar-files"></a>Arquivos de gramática TextMate

O LSP não incluem especificação sobre como fornecer coloração de texto para idiomas. Para fornecer a colorização personalizada para idiomas no Visual Studio, os desenvolvedores de extensão podem usar um arquivo de gramática TextMate. Para adicionar arquivos personalizados de gramática ou tema TextMate, siga estas etapas:

1. Crie uma pasta chamada "Gramáticas" dentro de sua extensão (ou pode ser qualquer nome que você escolher).

2. Dentro da pasta "Gramáticas", inclua qualquer *.tmlanguage, *.plist, *.tmtheme ou os arquivos *. JSON você gostaria que fornece colorização personalizada.

3. Clique com botão direito nos arquivos e selecione **propriedades**. Altere a ação de compilação para **conteúdo** e **incluir VSIX** propriedade como true.

4. Crie um arquivo .pkgdef e adicione uma linha semelhante a este:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Clique com botão direito nos arquivos e selecione **propriedades**. Altere a ação de compilação para **conteúdo** e **incluir VSIX** propriedade como true.

Depois de concluir as etapas anteriores, uma pasta de "Gramáticas" é adicionada à instalação do pacote diretório como uma fonte de repositório denominado 'MyLang' ('MyLang' é apenas um nome para ambiguidades e pode ser qualquer cadeia de caracteres exclusiva). Todas as gramáticas (.tmlanguage arquivos) e o tema (arquivos .tmtheme) nesse diretório são coletadas como potentials e substituem as gramáticas internas fornecidas com TextMate. Se as extensões declarado do arquivo de gramática correspondem à extensão do arquivo que está sendo aberto, TextMate será entrar.

## <a name="creating-a-simple-language-client"></a>Criando um cliente de linguagem simples

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interface principal - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Depois de criar seu projeto VSIX, adicione os seguintes pacotes do NuGet ao seu projeto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Ao assumir uma dependência do pacote do NuGet depois de concluir as etapas anteriores, os pacotes newtonsoft. JSON e StreamJsonRpc são adicionados ao seu projeto. **Não atualize esses pacotes, a menos que você tenha certeza de que as novas versões serão instaladas na versão do Visual Studio que suas metas de extensão**. Os assemblies não serão incluídos no seu VSIX – em vez disso, eles serão retirados do diretório de instalação do Visual Studio. Se você está fazendo referência a uma versão mais recente dos módulos do que a instalada no computador do usuário, a extensão *não funcionará*.

Você pode criar uma nova classe que implementa o [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interface, a principal interface necessário para clientes de idioma se conectar a um servidor de idioma LSP.

Este é um exemplo:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Os principais métodos que devem ser implementadas são [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) e [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) é chamado quando o Visual Studio carregou a sua extensão e o servidor de idioma estiver pronto para ser iniciada. Nesse método, você pode chamar o [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegado imediatamente para sinalizar que o servidor de idioma deve ser iniciado, ou você pode fazer lógica adicional e invocar [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) mais tarde. **Para ativar o servidor de idioma, você deve chamar StartAsync em algum momento.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) é o método invocado eventualmente chamando o [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegar; ele contém a lógica para iniciar o servidor de idioma e estabelecer conexão a ele. Um objeto de conexão que contém fluxos de gravação para o servidor e a leitura do servidor deve ser retornado. As exceções geradas aqui são detectadas e exibidas ao usuário por meio de uma mensagem de barra de informações no Visual Studio.

### <a name="activation"></a>Ativação

Depois de sua classe de cliente de idioma é implementada, você precisará definir dois atributos para ele para definir como ele será carregado no Visual Studio e ativado:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

O Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) para gerenciar seus pontos de extensibilidade. O [exportar](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) atributo indica para o Visual Studio que essa classe deve ser entregue como um ponto de extensão e carregada no momento apropriado.

Para usar MEF, você também deve definir MEF como um ativo no manifesto do VSIX.

Abra o designer de manifesto do VSIX e navegue até o **ativos** guia:

![Adicionar MEF ativo](media/lsp-add-asset.png)

Clique em novo para criar um novo ativo:

![definir o ativo MEF](media/lsp-define-asset.png)

* **Type**: Microsoft.VisualStudio.MefComponent
* **Origem**: um projeto na solução atual
* **Projeto**: [projeto]

### <a name="content-type-definition"></a>Definição de tipo de conteúdo

Atualmente, a única maneira de carregar a extensão de servidor seu idioma LSP é por tipo de conteúdo do arquivo. Ou seja, ao definir sua classe de cliente do idioma (que implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), será necessário definir os tipos de arquivos que, quando aberto, fará com que o carregamento da extensão. Se nenhum arquivo coincidir com o tipo de conteúdo definido aberto, a sua extensão não será carregada.

Isso é feito por meio da definição de uma ou mais classes de ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

No exemplo anterior, uma definição de tipo de conteúdo é criada para arquivos que terminam em `.bar` extensão de arquivo. A definição de tipo de conteúdo é fornecida a barra"name" e **deve** derivam [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Depois de adicionar uma definição de tipo de conteúdo, você pode definir quando carregar sua extensão de cliente do idioma na classe do idioma do cliente:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Adicionando suporte para servidores de idioma LSP não exige que você implementar seu próprio sistema de projeto no Visual Studio. Os clientes podem abrir um único arquivo ou uma pasta no Visual Studio para começar a usar o serviço de linguagem. Na verdade, o suporte para servidores de idioma LSP foi projetado para funcionar apenas em cenários de pasta/arquivos abertos. Se um sistema de projeto personalizado é implementado, alguns recursos (como configurações) não funcionará.

## <a name="advanced-features"></a>Recursos avançados

### <a name="settings"></a>Configurações

Há suporte para configurações específicas do servidor de idioma está disponível para a versão de visualização do suporte LSP no Visual Studio, mas ele ainda está sendo aperfeiçoada. As configurações são específicas que dá suporte a servidor de idioma e geralmente controlam como o servidor de idioma emite os dados. Por exemplo, um servidor de idioma pode ter uma configuração para o número máximo de erros relatados. Os autores de extensão deve definir um valor padrão, que pode ser alterado pelos usuários para projetos específicos.

Siga estas etapas abaixo para adicionar suporte para configurações para sua extensão de serviço de linguagem LSP:

1. Adicione um arquivo JSON (por exemplo, "MockLanguageExtensionSettings.json") em seu projeto que contém as configurações e seus valores padrão. Por exemplo:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Clique com o botão direito no arquivo JSON e selecione **propriedades**. Alterar o **criar** ação para "Conteúdo" e "incluir VSIX ' propriedade como true.

3. Implementar ConfigurationSections e retornar a lista de prefixos para as configurações definidas no arquivo JSON (no código do Visual Studio, ele seria mapeado para o nome da seção de configuração em Package. JSON):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Adicionar um arquivo .pkgdef ao projeto (Adicionar um novo arquivo de texto e altere a extensão de arquivo para .pkgdef). O arquivo do pkgdef deve conter estas informações:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Clique com o botão direito no arquivo .pkgdef e selecione **propriedades**. Alterar o **criar** ação "Conteúdo" e a propriedade "Incluir no VSIX" como true.

6. Abra o `source.extension.vsixmanifest` de arquivos e adicionar um ativo no **ativo** guia:

  ![Editar vspackage ativo](media/lsp-add-vspackage-asset.png)

  * **Tipo**: Microsoft.VisualStudio.VsPackage
  * **Origem**: arquivo no sistema de arquivos
  * **Caminho**: [caminho do arquivo pkgdef]

### <a name="user-editing-of-settings-for-a-workspace"></a>Usuário de edição de configurações para um espaço de trabalho

1. Usuário abre um espaço de trabalho que contém arquivos de que seu servidor possui.
2. Usuário adiciona um arquivo na pasta "vs" chamada "VSWorkspaceSettings.json".
3. Usuário adiciona uma linha para o arquivo VSWorkspaceSettings.json para uma configuração de que servidor fornece. Por exemplo:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>Habilitar o rastreamento de diagnóstico
Rastreamento de diagnóstico pode ser habilitado para todas as mensagens entre o cliente e servidor, que pode ser útil ao depurar problemas de saída.  Para habilitar o rastreamento de diagnóstico, faça o seguinte:

1. Abra ou crie o arquivo de configurações de espaço de trabalho "VSWorkspaceSettings.json" (consulte "Usuário edição de configurações para um espaço de trabalho").
2. Adicione a seguinte linha no arquivo de configurações de json:

```json
{
    "foo.server.trace": "Off"
}
```

Há três valores possíveis para o detalhamento do rastreamento:
* "Desligado": rastreamento desativado completamente
* "Messages": ID único método de nome e a resposta, mas o rastreamento ativado é rastreada.
* "Detalhado": o rastreamento ativado; a mensagem rpc inteira é rastreada.

Quando o rastreamento está ativado o conteúdo é gravado em um arquivo no diretório "% temp%\VisualStudio\LSP".  O log segue o formato de nomenclatura `[LanguageClientName]-[Datetime Stamp].log`.  Atualmente, o rastreamento pode ser habilitado somente para cenários de abrir a pasta.  Abrir um único arquivo para ativar um servidor de linguagem não tem suporte de rastreamento de diagnóstico.

### <a name="custom-messages"></a>Mensagens personalizadas

Existem APIs em vigor para facilitar a transmissão de mensagens para e recebendo mensagens do servidor de idioma que não fazem parte do protocolo de servidor de idioma padrão. Para tratar mensagens personalizadas, implementar [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interface em sua classe de cliente de idioma. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) biblioteca é usada para transmitir mensagens personalizadas entre o cliente de idioma e o servidor de idioma. Como sua extensão de cliente do idioma LSP assim como qualquer outra extensão do Visual Studio, você pode optar por adicionar recursos adicionais (que não são suportados pelo LSP) para o Visual Studio (usando outras APIs do Visual Studio) em sua extensão por meio de mensagens personalizadas.

#### <a name="receiving-custom-messages"></a>Recebendo mensagens personalizadas

Para receber mensagens personalizadas do servidor de idioma, implementar a [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) propriedade [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) e retornar um objeto que sabe como tratar suas mensagens personalizadas . Exemplo abaixo:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Enviando mensagens personalizadas

Para enviar mensagens personalizadas para o servidor de idioma, implementar a [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) método [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Esse método é chamado quando o servidor de idioma foi iniciado e está pronto para receber mensagens. Um [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objeto é passado como um parâmetro, que, em seguida, você pode manter para enviar mensagens para o servidor de idioma usando [StreamJsonRpc VS](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) APIs. Exemplo abaixo:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Camada intermediária

Às vezes, um desenvolvedor de extensão pode querer interceptar LSP mensagens enviadas e recebidas do servidor de idioma. Por exemplo, um desenvolvedor de extensão pode querer alterar o parâmetro da mensagem enviado para uma determinada mensagem LSP ou modificar os resultados retornados do servidor de idioma para um recurso LSP (por exemplo, conclusões). Quando isso for necessário, os desenvolvedores de extensão podem usar a API MiddleLayer intercepte mensagens LSP.

Cada mensagem LSP tem sua própria interface de camada intermediária para interceptação. Para interceptar uma mensagem específica, crie uma classe que implementa a interface de camada intermediária para essa mensagem. Em seguida, implementar a [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) em sua classe de cliente do idioma da interface e retornar uma instância do objeto no [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) propriedade. Exemplo abaixo:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

O recurso de camada intermediária é ainda em desenvolvimento e não ainda abrangente.

## <a name="sample-lsp-language-server-extension"></a>Extensão de servidor do exemplo LSP idioma

Para ver o código-fonte de uma extensão de exemplo usando a API de cliente LSP no Visual Studio, consulte exemplos de extensibilidade de VSSDK [exemplo LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Perguntas Frequentes

**Gostaria de criar um sistema de projeto personalizados para complementar o meu servidor de idioma LSP para oferecer suporte a recursos mais avançado no Visual Studio, como posso fazer isso?**

Suporte para servidores de idioma LSP no Visual Studio depende de [recurso Abrir pasta](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) e foi projetado especificamente para não exigem um sistema de projeto personalizados. Você pode criar seu próprio sistema de projeto personalizados seguindo instruções [aqui](https://github.com/Microsoft/VSProjectSystem), mas alguns recursos, como configurações, podem não funcionar. A lógica de inicialização padrão para servidores de idioma LSP é passar o local da pasta raiz da pasta que está sendo aberto no momento, portanto, se você usar um sistema de projeto personalizado, talvez seja necessário fornecer lógica personalizada durante a inicialização para garantir que seu servidor de idioma pode inicie corretamente.

**Como adicionar o suporte do depurador?**

Forneceremos suporte para o [comuns de depuração protocolo](https://code.visualstudio.com/docs/extensionAPI/api-debugging) em uma versão futura.

**Se já houver um VS idiomas com suporte serviço instalado (por exemplo, o JavaScript), eu ainda poderá instalar uma extensão de servidor de idioma LSP que oferece recursos adicionais (como linting)?**

Sim, mas nem todos os recursos funcionará corretamente. O objetivo final para extensões de servidor do idioma LSP é habilitar os serviços de idioma não suportados pelo Visual Studio. Você pode criar extensões que oferecem suporte adicional usando LSP idioma servidores, mas alguns recursos (como IntelliSense) não será uma experiência positiva. Em geral, é recomendável que as extensões de servidor de idioma LSP serem usadas para fornecer novas experiências de idioma, estendendo não existentes.

**Onde publicar meu servidor de idioma LSP concluído VSIX?**

Consulte as instruções do Marketplace [aqui](walkthrough-publishing-a-visual-studio-extension.md).
