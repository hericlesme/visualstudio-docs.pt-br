---
title: "Passo a passo: Implementando trechos de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc6fbfee6ab64cb50c03c55604db969e8ffc2d9d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-implementing-code-snippets"></a>Passo a passo: Implementando trechos de código
Você pode criar trechos de código e incluí-los em uma extensão de editor, para que os usuários da extensão podem adicioná-los para seu próprio código.  
  
 Um trecho de código é um fragmento de código ou outro texto que pode ser incorporado em um arquivo. Para exibir todos os trechos de código que tenham sido registrados para linguagens de programação específicas, no **ferramentas** menu, clique em **Gerenciador de trechos de código**. Para inserir um trecho de código em um arquivo, o botão direito do mouse em que você deseja que o trecho de código, clique em **Inserir trecho** ou **Surround With**, localize o trecho de código que você deseja e, em seguida, clique duas vezes nele. Pressione TAB ou SHIFT + TAB para modificar as partes relevantes do trecho de código e, em seguida, pressione ENTER ou ESC para aceitá-la. Para obter mais informações, consulte [Trechos de Código](../ide/code-snippets.md).  
  
 Um trecho de código está contido em um arquivo XML que tem a extensão de nome de arquivo. snippet. Um trecho de código pode conter campos que são realçados depois de inserido o trecho de código para que o usuário possa encontrar e alterá-los. Um arquivo de trecho de código também fornece informações para o **Gerenciador de trechos de código** para que ele possa exibir o nome do trecho de código na categoria correta. Para obter informações sobre o esquema do trecho de código, consulte [referência de esquema de trechos de código](../ide/code-snippets-schema-reference.md).  
  
 Este passo a passo ensina como realizar estas tarefas:  
  
1.  Crie e registre os trechos de código para um idioma específico.  
  
2.  Adicionar o **Inserir trecho** comando a um menu de atalho.  
  
3.  Implementar a expansão de trecho de código.  
  
 Este passo a passo se baseia [passo a passo: exibindo a conclusão de instrução](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Criando e registrando trechos de código  
 Normalmente, trechos de código são associados com um serviço de idioma registrados. No entanto, você não precisa implementar um <xref:Microsoft.VisualStudio.Package.LanguageService> para registrar os trechos de código. Em vez disso, especifique apenas um GUID no arquivo de índice de trecho de código e, em seguida, use o mesmo GUID de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que você adicionar ao seu projeto.  
  
 As etapas a seguir demonstram como criar trechos de código e associá-los com um GUID específico.  
  
1.  Crie a seguinte estrutura de diretório:  
  
     **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
     onde *InstallDir %* é a pasta de instalação do Visual Studio. (Embora esse caminho normalmente é usado para instalar os trechos de código, você pode especificar qualquer caminho.)  
  
2.  Na pasta \1033\, crie um arquivo. XML e nomeie- **TestSnippets.xml**. (Embora esse nome é normalmente usado para um arquivo de índice de trecho de código, você pode especificar qualquer nome desde que ele tenha uma extensão de nome de arquivo. XML.) Adicione o seguinte texto e, em seguida, excluir o espaço reservado de GUID e adicione seus próprios.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <SnippetCollection>  
        <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
            <SnippetDir>  
                <OnOff>On</OnOff>  
                <Installed>true</Installed>  
                <Locale>1033</Locale>  
                <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
                <LocalizedName>Snippets</LocalizedName>  
            </SnippetDir>  
        </Language>  
    </SnippetCollection>  
    ```  
  
3.  Criar um arquivo na pasta do trecho, nomeie-o **teste**`.snippet`e, em seguida, adicione o seguinte texto:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
        <CodeSnippet Format="1.0.0">  
            <Header>  
                <Title>Test replacement fields</Title>  
                <Shortcut>test</Shortcut>  
                <Description>Code snippet for testing replacement fields</Description>  
                <Author>MSIT</Author>  
                <SnippetTypes>  
                    <SnippetType>Expansion</SnippetType>  
                </SnippetTypes>  
            </Header>  
            <Snippet>  
                <Declarations>  
                    <Literal>  
                      <ID>param1</ID>  
                        <ToolTip>First field</ToolTip>  
                        <Default>first</Default>  
                    </Literal>  
                    <Literal>  
                        <ID>param2</ID>  
                        <ToolTip>Second field</ToolTip>  
                        <Default>second</Default>  
                    </Literal>  
                </Declarations>  
                <References>  
                   <Reference>  
                       <Assembly>System.Windows.Forms.dll</Assembly>  
                   </Reference>  
                </References>  
                <Code Language="TestSnippets">  
                    <![CDATA[MessageBox.Show("$param1$");  
         MessageBox.Show("$param2$");]]>  
                </Code>    
            </Snippet>  
        </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
 As etapas a seguir mostram como registrar os trechos de código.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Para registrar os trechos de código para um GUID específico  
  
1.  Abra o **CompletionTest** projeto. Para obter informações sobre como criar este projeto, consulte [passo a passo: exibindo a conclusão de instrução](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  No projeto, adicione referências para os seguintes assemblies:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  No projeto, abra o arquivo source.extension.vsixmanifest.  
  
4.  Verifique se o **ativos** guia contém uma **VsPackage** tipo e conteúdo **projeto** é definido como o nome do projeto.  
  
5.  Selecione o projeto CompletionTest e na janela Propriedades, defina **gerar arquivo de Pkgdef** para **true**. Salvar o projeto.  
  
6.  Adicionar um estático `SnippetUtilities` classe ao projeto.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Na classe SnippetUtilities, definir um GUID e atribua o valor usado no arquivo SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Adicionar o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> para o `TestCompletionHandler` classe. Esse atributo pode ser adicionado a qualquer classe de público ou interno (não estático) no projeto. (Você precisará adicionar um `using` instrução do namespace Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Compile e execute o projeto. Na instância experimental do Visual Studio que é iniciado quando o projeto é executado, o trecho de código que você acabou de registrar deve ser exibido no **Gerenciador de trechos de código** sob o **TestSnippets** idioma.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Adicionando o comando de trecho de código de inserção para o Menu de atalho  
 O **Inserir trecho** comando não está incluído no menu de atalho para um arquivo de texto. Portanto, você deve habilitar o comando.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para adicionar o comando Inserir trecho para o menu de atalho  
  
1.  Abra o `TestCompletionCommandHandler` arquivo de classe.  
  
     Como essa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, você pode ativar o **Inserir trecho** do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. Antes de ativar o comando, verifique se esse método não está sendo chamado dentro de uma função de automação porque quando o **Inserir trecho** comando é clicado, será exibida a interface do usuário trecho do seletor (IU).  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Compile e execute o projeto. Na instância experimental, abra um arquivo que tem a extensão de nome de arquivo. zzz e, em seguida, clique duas vezes nele. O **Inserir trecho** comando deve aparecer no menu de atalho.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementando o trecho de expansão no selecionador de trecho de código da interface do usuário  
 Esta seção mostra como implementar a expansão de trecho de código para que o selecionador de trecho de código da interface do usuário é exibido quando **Inserir trecho** é clicado no menu de atalho. Um trecho de código também é expandido quando um usuário digita o atalho de trecho de código e, em seguida, pressiona TAB.  
  
 Para exibir o seletor de trecho de código da interface do usuário e para permitir a navegação e aceitação de pós-inserção de trecho de código, use o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. A inserção em si é tratada pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> método.  
  
 A implementação de expansão de trecho de código usa herdado <xref:Microsoft.VisualStudio.TextManager.Interop> interfaces. Quando você converte de classes de editor atual para o código herdado, lembre-se de que as interfaces herdadas usar uma combinação de números de linha e coluna para especificar locais em um buffer de texto, mas as classes atuais usam um índice. Portanto, se um buffer tem três linhas cada um deles tem dez caracteres (mais de uma nova linha, que conta como 1 caractere), é o quarto caractere na terceira linha na posição 27 na implementação atual, mas ele está na linha 2, posicione 3 na implementação do antiga.  
  
#### <a name="to-implement-snippet-expansion"></a>Para implementar a expansão de trecho de código  
  
1.  Para o arquivo que contém o `TestCompletionCommandHandler` de classe, adicione o seguinte `using` instruções.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Verifique o `TestCompletionCommandHandler` classe implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  No `TestCompletionCommandHandlerProvider` classe, importe o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Adicionar alguns campos particulares para as interfaces de expansão de código e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  No construtor do `TestCompletionCommandHandler` classe, defina os campos a seguir.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Para exibir o seletor de trecho de código quando o usuário clica o **Inserir trecho** de comando, adicione o seguinte código para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. (Para tornar esta explicação mais legível, o código de EXEC () que é usado para a conclusão de instrução não é mostrado; em vez disso, os blocos de código são adicionados para o método existente). Adicione o seguinte bloco de código após o código que verifica se há um caractere.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Se um trecho de código tem campos que podem ser navegados, a sessão de expansão é mantida aberta até que a expansão é aceito explicitamente; Se o trecho de código não tem campos, a sessão é fechada e será retornada como `null` pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> método. No <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método, após o seletor de trecho de código de interface do usuário que você adicionou na etapa anterior, adicione o seguinte código para lidar com navegação de trecho de código (quando o usuário pressionar TAB ou SHIFT + TAB após a inserção de trecho de código).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Para inserir o trecho de código, quando o usuário digita o atalho correspondente e, em seguida, pressiona TAB, adicione código para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. O método particular que insere o trecho de código será mostrado em uma etapa posterior. Adicione o seguinte código após o código de navegação que você adicionou na etapa anterior.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementar os métodos do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface. Nessa implementação, os únicos métodos de interesse são <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Os outros métodos devem retornar apenas <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementar o método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . O método auxiliar que realmente insere as expansões será abordado em uma etapa posterior. O <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> fornece informações de linha e coluna, que você pode obter por meio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. O método privado a seguir insere um trecho de código, com base no atalho ou no título e no caminho. Depois, ele chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> método com o trecho de código.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Compilar e testar a expansão de trecho de código  
 Você pode testar se funciona de expansão de trecho em seu projeto.  
  
1.  Compile a solução. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
2.  Abra um arquivo de texto e digite algum texto.  
  
3.  Clique em algum lugar no texto e, em seguida, clique em **Inserir trecho**.  
  
4.  O seletor de trecho de interface do usuário deve aparecer com um pop-up informando que **campos de substituição de teste**. Clique duas vezes o pop-up.  
  
     O trecho a seguir deve ser inserido.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Não pressione ENTER ou ESC.  
  
5.  Pressione TAB e SHIFT + TAB para alternar entre "primeira" e "segundo".  
  
6.  Aceite a inserção pressionando ENTER ou ESC.  
  
7.  Em uma parte diferente do texto, digite "teste" e, em seguida, pressione TAB. Como "teste" é o atalho de trecho de código, o trecho de código deve ser inserido novamente.  
  
## <a name="next-steps"></a>Próximas etapas